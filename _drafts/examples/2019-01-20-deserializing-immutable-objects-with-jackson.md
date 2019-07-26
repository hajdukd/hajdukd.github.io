---
permalink: /tech/:title
---

TL;DR for immutability or rather immutable objects is that after the creation, the state of those objects cannot be changed.
This is highly useful in multi-threaded environments. Imagine an object shared between multiple threads, each performing operations
using this object in an unknown order while in between the state of that object changes.

Results of such operations would be completely unpredictable and tracking such bugs would be really challenging.
But when _you know_ your shared objects state cannot be modified no matter what.. that solves all of those problems!

## Immutable objects deserialization with Jackson

Now that you know what immutable objects are and what they can be used for, it is the moment to talk about some nuances connected to them. This time it will be _deserialization_.
The library i would like to put in the spotlight is Jackson - for most known as "JSON parser for Java" (it actually represents a lot more but it's not the point of this post).

There are few ways one can choose to deserialize JSON to an immutable object using Jackson:

 - Constructor annotated as [@JsonCreator](https://fasterxml.github.io/jackson-annotations/javadoc/2.7/com/fasterxml/jackson/annotation/JsonCreator.html) - requires you to take in all required parameters and annotate them with [@JsonProperty](https://fasterxml.github.io/jackson-annotations/javadoc/2.7/com/fasterxml/jackson/annotation/JsonProperty.html).
 A lot of boilerplate code and numb solution.


```
    @JsonCreator(mode = JsonCreator.Mode.PROPERTIES)
    public User(@JsonProperty("id") Long id,
                @JsonProperty("firstName") String firstName,
                @JsonProperty("lastName") String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }
```
 - Constructor annotated with [@ConstructorProperties](https://docs.oracle.com/javase/8/docs/api/java/beans/ConstructorProperties.html) (Jackson 2.7.0+) - similar to @JsonCreator but limits the number of boilerplate to specifying only properties (order matters).


```
    @ConstructorProperties({"id", "firstName", "lastName"})
    public User(Long id,
                String firstName,
                String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }
```
- Custom _deserializer_ - custom implementation of [StdDeserializer](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/deser/std/StdDeserializer.html), which can be registered via [@JsonDeserialize](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/annotation/JsonDeserialize.html) annotation on an immutable object class or via mapper module deserializer registration.


```
    public class UserDeserializer extends StdDeserializer<User> {
    
        public UserDeserializer() {
            super(User.class);
        }
    
        @Override
        public User deserialize(JsonParser jsonParser, DeserializationContext deserializationContext) throws IOException, JsonProcessingException {
            //...
        }
    }
```
- Custom mix-in - which uses similar approach to @JsonCreator but is registered differently ([docs](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/ObjectMapper.html#addMixIn(java.lang.Class,%20java.lang.Class)). This one is especially good in case you have no ownership on immutable object class and cannot extend it.


```
    public abstract class UserMixIn {

        UserMixIn(@JsonProperty("id") Long id,
                  @JsonProperty("firstName") String firstName,
                  @JsonProperty("lastName") String lastName) {
        }
    }
```
- Builder annotated with [@JsonPOJOBuilder](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/annotation/JsonPOJOBuilder.html) registered via @JsonDeserialize annotation on an immutable object class - this is my favourite method.
It solves not only the problem of deserialization, but also allows for optional fields, optional values and frees us from cumbersome @JsonProperty annotation on every param in constructor.


```
    @Value
    @Builder(builderClassName = "Builder")
    @JsonDeserialize(builder = User.Builder.class)
    public class User {
    
        private Long id;
        private String firstName;
        private String lastName;
    
        @JsonPOJOBuilder(withPrefix = "")
        public static class Builder {
        }
    }
```

_FYI: Boilerplate code connected to immutability (fields effectively private and final, getters only, all arguments constructor) were all generated by Lombok's [@Value](https://projectlombok.org/features/Value). Builder with class name "Builder" on the other hand was generated via [@Builder](https://projectlombok.org/features/Builder) annotation.
If you are not familiar with Lombok i would highly recommend checking it out. [Here](https://projectlombok.org/) you can find the project site._

Out of all of presented solutions, like i said, my favourite is the builder pattern. But it's worth noting that each one of those has a unique use case. For mix-in it was the lack of extension possibilities.

Find by yourself what suits your use case the best.

Samples source code can be found on my [github](https://github.com/hajdukd/samples/tree/master/immutabledeserializationjacksonsample).