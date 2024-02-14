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
**Bugged**
```java
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }
```
**Fixed**
```java
static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }
```
**Explanation**
By incrementing `index2` instead of `index1` in the third while loop, the while loop will properly terminate and merge the rest of the contents of `list2`, thus avoiding the OutOfMemoryError given previously.



