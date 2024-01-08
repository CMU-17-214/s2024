# Lab 10 - Testing in the Real World

This recitation is an introduction to test doubles.

## Deliverables
- [ ] Use a fake to test `logIn`
- [ ] Use stubs to test `getRecommendation`
- [ ] Use mocks to test `sendPromoEmail`

## Introduction

In testing, it may sometimes be necessary to use objects or procedures that look and behave like their release-intended counterparts but are actually simplified versions that reduce the complexity and facilitate testing. Objects or procedures meant for production can be too slow, unavailable, expensive, opaque, or non-deterministic. Instead, test doubles are often used. There are multiple types of test doubles, but the most well-known/popular are Fakes, Stubs, and Mocks.

### Fakes

Fakes are fully functional classes with a simplified implementation. Usually, they take some shortcuts and are a simplified version of the real object. We use fakes to avoid interacting directly with objects that are too costly to access during testing, like databases. So, instead of querying our actual database, we use a fully functional in-memory database to simulate the same operations.

<!-- ![Fakes](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*snrzYwepyaPu3uC9.png) -->

### Stubs

A stub is an artificial class that returns pre-configured data. We use it to answer calls during tests. Stubs are used when we can't or don’t want to involve objects that would answer with real data or would have undesirable side effects. For example, instead of querying our real database, we may use a stub with predefined data to simulate only the functionality we need.

<!-- ![Stubs](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*KdpZaEVy6GNnrUpB.png) -->

### Mocks

A mock is an instrumented variant of a real class with fine-grained control. We use mocks when we don’t want to invoke expensive production code or when there is no easy way to verify that an intended action was executed. For example, we don't want to send a new email every time we want to test an email system.

<!-- ![Mocks](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*k7mwTF60slyMxRlm.png) -->

These three terms are usually used interchangeably in practice, but there are some subtle differences. You can find plenty of resources online that go into more detail on the differences if you're still unsure what they are (don't worry, even experienced software developers get it [wrong](https://martinfowler.com/articles/mocksArentStubs.html)).

## Instructions

Clone the AndrewWS repository from https://github.com/CMU-17-214/f23-lab10. Run the following commands to get started:
```
mvn install
mvn test
```
You might notice the tests are taking a very long time to run. Let's increase their performance using test doubles! Look through the provided files to see which methods you will need to test with which types of test doubles. You will find hints on how to proceed there.

All of your tests should be written in `AndrewWebServicesTest.java`. You will also need to implement a fake database in `InMemoryDatabase.java`. For mocks, we will use the [Mockito](https://site.mockito.org/) framework.

## Mockito

We will be using the mocking framework [Mockito](https://site.mockito.org/) in this lab. Here is a simple example to get you familiar with the important parts of Mockito.

We'll use the `Cartoons` class for this example. The `Cartoons` class represents a mapping from characters to the cartoons they belong to.
```
public class Cartoons {
	private Map<String, String> charactersToCartoons;

	public String get(String character) {
		return charactersToCartoons.get(character);
	}
}
```
We use the `mock` method to create a mock of `Cartoons`:
```
Cartoons ourMock = mock(Cartoons.class);
```

Now we can use the `when` and `thenReturn` methods to add behavior to our mocked class (aka stub a method call):

```
when(ourMock.get("Snoopy")).thenReturn("Peanuts");
```

So, we've specified that whenever we call `get("Snoopy")`, our mocked class should return "Peanuts".

Next, we execute a method call on our mock:
```
String snoopyCartoon = ourMock.get("Snoopy");
```

Now we use the `verify` method to check that our method was called with the given arguments. The following lines confirm that we invoked the `get` method on the mock and that the method returned a value that matches the expectation we set before:
```
verify(ourMock).get("Snoopy");
assertEquals(snoopyCartoon, "Peanuts")
```

So, now we've successfully mocked the `Cartoons` class and used a stub method call to write a test for the `get` method in `Cartoons`.

This example covered everything you need to know for mocks in this lab. Feel free to checkout the [Mockito website](https://site.mockito.org/) for more information and documentation on the methods we used above, or look online for other examples using Mockito if the one above wasn't clear. Also, ask your TAs or ask on Piazza if you need any further help. Good luck!