# Module 4 : Using Framework for Validation
Course slides : [link](https://github.com/HeithemLejmi/DefensiveCoding/blob/main/courses/module4_using-frameworks-for-validation-slides.pdf)

## Objects API
- It is a native Java API, that has several interesting methods that we can use to validate our inputs:
  - Like `requireNonNull(param, msg)` which take a param to be validated as non-null, and a msg to be displayed if this 
    param found to be null:
```java
public Booking(String referenceId, List<Passenger> passengers, Flight flight){
  this.referenceId = isInvalidString(referenceId);
  this.passengerList = validateList(passengers);
  // Using Objects API :
  this.flight = Objects.requireNonNull(flight, "A booking cannot be created with a Flight null reference");
}

```

## Hibernate validator:
- The hibernate validator framework allow you to reinforce constraints on fields withing a java class (like in the 
  [FlightWithAnnotations](src/main/java/com/defcoding/entities/FlightWithAnnotations.java) class) are :
  - `@NotNull` : a constrained CharSequence, Collection, Map, or Array is valid as long as it's not null, but it can be empty
  - `@NotEmpty` : a constrained CharSequence, Collection, Map, or Array is valid as long as it's not null and its 
    size/length is greater than zero
  - `@NotBlank`: a constrained String is valid as long as it's not null, and the trimmed length is greater than zero
  - `@Range(min=${},max=${})`: which defines the minimum, and the max values that a numerical field could have.
