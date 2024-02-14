# Lab Report 3
## Failure Inducing Test 
```java
@Test
  public void failureTestMerge(){
    ArrayList<String> list1 = new ArrayList<>();
    ArrayList<String> list2 = new ArrayList<>();
    list1.add("a");
    list1.add("c");
    list1.add("e");
    list2.add("b");
    list2.add("d");
    list2.add("f");

    ArrayList<String> expected= new ArrayList<>();
    expected.add("a");
    expected.add("b");
    expected.add("c");
    expected.add("d");
    expected.add("e");
    expected.add("f");

    assertEquals(expected,ListExamples.merge(list1,list2));
  }
```
**Symptom**
![Image](/images/lr5.1.png)
## Non-failure Inducing Test
```java
@Test
  public void successTestMerge(){
    ArrayList<String> list1 = new ArrayList<>();
    ArrayList<String> list2 = new ArrayList<>();
    list1.add("a");
    list1.add("c");
    list1.add("e");
    list1.add("g");
    list2.add("b");
    list2.add("d");
    list2.add("f");

    ArrayList<String> expected = new ArrayList<>();
    expected.add("a");
    expected.add("b");
    expected.add("c");
    expected.add("d");
    expected.add("e");
    expected.add("f");
    expected.add("g");
    assertEquals(expected, ListExamples.merge(list1,list2));
  }
```
**Symptom**
![Image](/images/lr5.2.png)
## The Bug
**Before**


