# Mocking methods that take primitive arguments throws NullPointerException

We want to mock method of an object that takes a primitive as argument.
```java
class WantToMock {
  public Something returnSomething(int primtiveArgument) {
    //...
  }
}
```

In our unit test we want to mock a method so that it always returns specified value no matter what the input argument is.
It seems logical to do something like this:
```java
WantToMock mockedObject = mock(WantToMock.class);

var wantToReturn = new Something();

when(mockedObject.returnSomething(any()).thenReturn(wantToReturn);
```

Executing last line will throw a NullPointerException.

Reasons are detailed [here](https://stackoverflow.com/questions/33124153/mockito-nullpointerexception-when-stubbing-method)

To remedy situation, instead of ```any()``` we have to use ```anyInt()```
