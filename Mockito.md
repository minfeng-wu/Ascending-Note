## Spring Profiles:
@Profile("dev")

Set Profile
如果不match， new了在memory里面但是不再spring container里面

## Stub:
predefined data, fake class with pre=programmed return values, return dummy object,里面全部method return dummy object

## Mock:
fake class, record how many times a method called, store method called record interaction between java classes. 同上+记录

## Spy:
Partially mock object. It means spy creates a partial object or a half dummy of the real object by stubbing or spying the real ones.
The real object remained unchange.

## example:
- Spying object sypAccountServiceObject  一开始，和真的一样，可以完成Mock的功能，
- Mocking object mockAccountServiceObject  instruct return values when a method of the mock object is called, example, List<Account> 可以return
  任何数量的dummy Account List，我可以控制return什么
- Stubling object stubAccountServiceObject
  
# Mockito:
-  Mock Object: dummy input, dummy return, loose the entire behavior of class
-  Mockito is a mocking framwork
-  Cannot mock static meothd, constructor, equals, hashcode, private method toString, only thread-safe in healy test.(Not thread-safe!!!)
-  Procedure: Mock dependencies for class under test -> execute code in the class under test -> Valide if code execute correctly
-  Test double: an object that can stand for a real object in a test(Sub, Mock or Mock or dummy object)

## Annotation:
- @Mock
- @Spy
- @InjectMock, 连结Mock object 一个mock object里面的如果有mock object，自动连结
- @Captor,to catch the verify value for further compare

## how to process all of its annotation
- Explicitly invoke MockitoAnnotation.initMocks(testClass) method in @Before
- @RunWith(MockitoJunitRunner.class) at the top of unit test class
- MockitoJunit.rule() to create MockitoRule class

## how to stub a spy object
- doReturn()  Unite test good practice:when***_then***
Mockito.doReturn(100).when(spyList).size(); spyList.size()永远就是100了
## verify
- Mockito.verify(mockedList).add("one") -> mockedList有没有加过“one”
- veryfy(test, time(2)).methodxxx
- never(), atMost(5), atLeast(3)
- verifyNoMoreInteraction(test)

## Mockito API
- Allows to configure the return values of its mocks via a fluent API
null -> object 0 -> number false -> boolean empty collection -> collectiion
- anyInt(), isAClass?
- when thenReturn
- when thenThrow()  @Test(expected = xxxexcpetion)
- doReturn when, doThrow when
- doReturn when, it will not call real method on spied object.
- when/thenReturn, it will call real method on spied object.
- when(spy.get(0))the...  spy.get(0) 真的call了
- doAnswer

## Builder Design Pattern
- public static class PizzaBuilder inner class
- same variable
- 空或者不空的constructor
- public PizzaBuilder name(String name) 所有方法都return PizzaBuilder
- public Pizza build(){return new Pizza(this)}
- out side private Pizza(PizzaBuilder pizzaBuilder){this.name = pizzaBuilder.name this.size = pizzaBuilder.size......}




