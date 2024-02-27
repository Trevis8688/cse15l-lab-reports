# Lab Report 3
## Part 1
### Failure Inducing Test 
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
### Non-failure Inducing Test
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
### The Bug
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
**Explanation** \
By incrementing `index2` instead of `index1` in the third while loop, the while loop will properly terminate and merge the rest of the contents of `list2`, thus avoiding the OutOfMemoryError given previously.

## Part 2
### grep command line options
1. The option `-i` makes the pattern searching case-insensitive meaning `"hello"` would match `"HELLO"`. (Source: GREP Manual Page)
2. The option `-r` makes the command find the given pattern recursively through every file/directory inside of the directory provided (Source: GREP Manual Page)
3. The option `-n` prints the associated line numbers next to the lines found that match the given pattern (Source: GREP Manual Page)
4. The option `-v` prints the lines that do not match the given pattern. (Source: GREP Manual Page)

### Examples of `-i` 

1. \
**Input:** `grep -i "september" ./911report/chapter-1.txt` \
**Output:**
`    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.`\
`    They were planning to hijack these planes and turn them into large guided missiles, loaded with up to 11,400 gallons of jet fuel. By 8:00 A.M. on the morning of Tuesday, September 11,2001, they had defeated all the security layers that America's civil aviation security system then had in place to prevent a hijacking. The Hijacking of American 11 American Airlines Flight 11 provided nonstop service from Boston to Los Angeles. On September 11, Captain John Ogonowski and First Officer Thomas McGuinness piloted the Boeing 767. It carried its full capacity of nine flight attendants. Eighty-one passengers boarded the flight with them (including the five terrorists).22 The plane took off at 7:59. Just before 8:14, it had climbed to 26,000 feet, not quite its initial assigned cruising altitude of 29,000 feet. All communications and flight profile data were normal. About this time the "Fasten Seatbelt" sign would usually have been turned off and the flight attendants would have begun preparing for cabin service.`\
`    The Hijacking of American 77 American Airlines Flight 77 was scheduled to depart from Washington Dulles for Los Angeles at 8:10. The aircraft was a Boeing 757 piloted by Captain Charles F. Burlingame and First Officer David Charlebois. There were four flight attendants. On September 11, the flight carried 58 passengers.`\
`    FAA Mission and Structure. As of September 11, 2001, the FAA was mandated by law to regulate the safety and security of civil aviation. From an air traffic controller's perspective, that meant maintaining a safe distance between airborne aircraft.`\
`    On the morning of September 11, Secretary Rumsfeld was having breakfast at the Pentagon with a group of members of Congress. He then returned to his office for his daily intelligence briefing. The Secretary was informed of the second strike in New York during the briefing; he resumed the briefing while awaiting more information. After the Pentagon was struck, Secretary Rumsfeld went to the parking lot to assist with rescue efforts.`\
`    There is no evidence that NORAD headquarters or military officials in the NMCC knew-during the morning of September 11-that the Andrews planes were airborne and operating under different rules of engagement.`\
`    The details of what happened on the morning of September 11 are complex, but they play out a simple theme. NORAD and the FAA were unprepared for the type of attacks launched against the United States on September 11, 2001. They struggled, under difficult circumstances, to improvise a homeland defense against an unprecedented challenge they had never before encountered and had never trained to meet.`\
**Explanation:**
Being provided the pattern "september", the `grep` command with the option `-i` returned all lines in the document that contained the pattern without case-sensitivity. In this case, lines with "September" were included. (Source: GREP Manual Page)\
2. \
**Input:** `grep -i "scooter" ./911report/chapter-1.txt`
**Output:** 
`  Among the sources that reflect other important events of that morning, there is no documentary evidence for this call, but the relevant sources are incomplete. Others nearby who were taking notes, such as the Vice President's chief of staff, Scooter Libby, who sat next to him, and Mrs. Cheney, did not note a call between the President and Vice President immediately after the Vice President entered the conference room.`\
`  His reaction was described by Scooter Libby as quick and decisive, "in about the time it takes a batter to decide to swing." The Vice President authorized fighter aircraft to engage the inbound plane. He told us he based this authorization on his earlier conversation with the President. The military aide returned a few minutes later, probably between 10:12 and 10:18, and said the aircraft was 60 miles out. He again asked for authorization to engage. The Vice President again said yes.`\
**Explanation:** Being provided the pattern "scooter", the `grep` command with the option `-i` returned all lines in the document that conatined the pattern without case-sensitivity. In this case, lines with "Scooter" were included. (Source: GREP Manual Page)

### Examples of `-r` 

1. \
**Input:**
`grep -r "Scooter" ./911report` \
**Output:**
`./911report/chapter-13.2.txt:            219. For Libby's characterization, see White House transcript, Scooter Libby`\
`./911report/chapter-1.txt:    Among the sources that reflect other important events of that morning, there is no documentary evidence for this call, but the relevant sources are incomplete. Others nearby who were taking notes, such as the Vice President's chief of staff, Scooter Libby, who sat next to him, and Mrs. Cheney, did not note a call between the President and Vice President immediately after the Vice President entered the conference room. `\
`./911report/chapter-1.txt:    His reaction was described by Scooter Libby as quick and decisive, "in about the time it takes a batter to decide to swing." The Vice President authorized fighter aircraft to engage the inbound plane. He told us he based this authorization on his earlier conversation with the President. The military aide returned a few minutes later, probably between 10:12 and 10:18, and said the aircraft was 60 miles out. He again asked for authorization to engage. The Vice President again said yes.` \
**Explanation:** Being provided the pattern "Scooter", the `grep` command with the option `-r` searched all files and subdirectories of the directory `./911report` that matched the pattern. (Source: GREP Manual Page) \

2. \
**Input:** `grep -r "Jane Garvey" ./911report`\
**Output:**
`./911report/chapter-13.2.txt:            181. Jane Garvey interview (Jun. 30, 2004); Monte Belger interview (Apr. 20, 2004).`\
`./911report/chapter-13.2.txt:            190. Patrick Gardner interview (May 12, 2004). For participants, see Jane Garvey`\
`./911report/chapter-13.3.txt:                Priorities,"Mar. 18, 1999 (staff working paper). See also Jane Garvey prepared`\
`./911report/chapter-13.3.txt:                informed on any pressing issues. Jane Garvey interview (Oct. 21, 2003); Monte Belger`\
`./911report/chapter-13.3.txt:            63. Jane Garvey interview (Oct. 21, 2003).`\
`./911report/chapter-3.txt:                agency's leadership. Neither Administrator Jane Garvey nor her deputy routinely`\
`./911report/chapter-1.txt:    Within the FAA, the administrator, Jane Garvey, and her acting deputy, Monte Belger, had not been told of a confirmed hijacking before they learned from television that a plane had crashed.`\
**Explanation:** Being provided the pattern "Jane Garvey", the `grep` command with the option `-r` searched all files and subdirectories of the directory `./911report` that matched the pattern. (Source: GREP Manual Page) \

### Examples of `-n`
1. \
**Input:** `grep -n "September" ./911report/chapter-1.txt` \
**Output:**
```
    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
    They were planning to hijack these planes and turn them into large guided missiles, loaded with up to 11,400 gallons of jet fuel. By 8:00 A.M. on the morning of Tuesday, September 11,2001, they had defeated all the security layers that America's civil aviation security system then had in place to prevent a hijacking. The Hijacking of American 11 American Airlines Flight 11 provided nonstop service from Boston to Los Angeles. On September 11, Captain John Ogonowski and First Officer Thomas McGuinness piloted the Boeing 767. It carried its full capacity of nine flight attendants. Eighty-one passengers boarded the flight with them (including the five terrorists).22 The plane took off at 7:59. Just before 8:14, it had climbed to 26,000 feet, not quite its initial assigned cruising altitude of 29,000 feet. All communications and flight profile data were normal. About this time the "Fasten Seatbelt" sign would usually have been turned off and the flight attendants would have begun preparing for cabin service.
    The Hijacking of American 77 American Airlines Flight 77 was scheduled to depart from Washington Dulles for Los Angeles at 8:10. The aircraft was a Boeing 757 piloted by Captain Charles F. Burlingame and First Officer David Charlebois. There were four flight attendants. On September 11, the flight carried 58 passengers.
    FAA Mission and Structure. As of September 11, 2001, the FAA was mandated by law to regulate the safety and security of civil aviation. From an air traffic controller's perspective, that meant maintaining a safe distance between airborne aircraft.
    On the morning of September 11, Secretary Rumsfeld was having breakfast at the Pentagon with a group of members of Congress. He then returned to his office for his daily intelligence briefing. The Secretary was informed of the second strike in New York during the briefing; he resumed the briefing while awaiting more information. After the Pentagon was struck, Secretary Rumsfeld went to the parking lot to assist with rescue efforts.
    There is no evidence that NORAD headquarters or military officials in the NMCC knew-during the morning of September 11-that the Andrews planes were airborne and operating under different rules of engagement.
    The details of what happened on the morning of September 11 are complex, but they play out a simple theme. NORAD and the FAA were unprepared for the type of attacks launched against the United States on September 11, 2001. They struggled, under difficult circumstances, to improvise a homeland defense against an unprecedented challenge they had never before encountered and had never trained to meet.
```
**Explanation:** Being provided the pattern "September", the `grep` command with the option `-n` returned all lines in the document that contained the pattern along with the line number. (Source: GREP Manual Page) \

2. \
**Input:** `grep -n "Scooter" ./911report/chapter-1.txt` \
**Output:** 
`640:    Among the sources that reflect other important events of that morning, there is no documentary evidence for this call, but the relevant sources are incomplete. Others nearby who were taking notes, such as the Vice President's chief of staff, Scooter Libby, who sat next to him, and Mrs. Cheney, did not note a call between the President and Vice President immediately after the Vice President entered the conference room.`\
`646:    His reaction was described by Scooter Libby as quick and decisive, "in about the time it takes a batter to decide to swing." The Vice President authorized fighter aircraft to engage the inbound plane. He told us he based this authorization on his earlier conversation with the President. The military aide returned a few minutes later, probably between 10:12 and 10:18, and said the aircraft was 60 miles out. He again asked for authorization to engage. The Vice President again said yes.`\
**Explanation:** Being provided the pattern "Scooter", the `grep` command with the option `-n` returned all lines in the document that contained the pattern along with the line number. (Source: GREP Manual Page) \

### Examples of `-v`
1. \
**Input:** `grep -v "we" ./plos/pmed.0020028.txt >grep.txt` \
**Output:**

        Dr. Gerberding outlines critical steps for arresting the HIV/AIDS epidemic [1]. She
        suggests moving ahead with “ABCs” and with “D” for diagnosis and “R” for responsibility.
        These are good suggestions—with increased HIV testing and individuals taking responsibility
        immediately implement the mainstays of public health—universal testing and contact tracing
        [2,3,4]. Every sexually active individual and every individual at risk for HIV deserves to
        know their HIV status. Thus, every HIV-infected individual must be called upon to be
        accountable for preventing HIV transmission. Contact tracing should be instituted for HIV
        just as it is for other infectious diseases. Those who have been exposed to HIV have a
        right to know how to protect themselves and if they too are infected, to be offered
        treatment [5]. HIV testing has too often focused on testing of women in a perinatal setting
        rather than universal testing in routine clinical care. Without universal voluntary HIV
        now at 55% of all HIV infections and in all likelihood at 75%–80% in another 8 to 10 years
        [6,7]. For too long the debate has been that contact tracing will result in physical abuse
        of women. Confining our definition of abuse of women to physical abuse alone is to have too
        narrow an ethical focus—HIV infection itself is an abuse of women or of anyone else.
        Universal HIV testing and contact tracing adds an essential comprehensive public health
        approach to the epidemic that will be successful in reducing the ever-escalating numbers of
        new infections.
  **Explanation:** Being provided the pattern "we", the `grep` command with the option `-v` returned all lines that did not contain the pattern "we". (Source: GREP Manual Page)\

2. \
**Input:** `grep -v "and" ./plos/pmed.0020028.txt >grep.txt` \
**Output:**
      
        Dr. Gerberding outlines critical steps for arresting the HIV/AIDS epidemic [1]. She
        for their role in HIV spread, the epidemic might be slowed. We could continue to add
        incrementally to the alphabet soup of public health. But instead, we could choose to
        know their HIV status. Thus, every HIV-infected individual must be called upon to be
        accountable for preventing HIV transmission. Contact tracing should be instituted for HIV
        just as it is for other infectious diseases. Those who have been exposed to HIV have a
        treatment [5]. HIV testing has too often focused on testing of women in a perinatal setting
        rather than universal testing in routine clinical care. Without universal voluntary HIV
        [6,7]. For too long the debate has been that contact tracing will result in physical abuse
        of women. Confining our definition of abuse of women to physical abuse alone is to have too
        narrow an ethical focus—HIV infection itself is an abuse of women or of anyone else.
        approach to the epidemic that will be successful in reducing the ever-escalating numbers of
        new infections.
   
**Explanation:** Being provided the pattern "and", the `grep` command with the option `-v` returned all lines that did not contain the pattern "and" (Source: GREP Manual Page).











