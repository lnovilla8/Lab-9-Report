# Lab Report 9

## Student Post

Hi everyone,
I am working on a filter method that is used to extract a certain string from an array list. My first test works correctly, 
but on my second tests, I do not get the expected output. I ran ```bash test.sh``` which has the command ```java -cp .:lib/* org.junit.runner.JUnitCore TestListExamples```. Any thoughts on how to fix this bug?

```TestExamples.java```
```
import static org.junit.Assert.*; 
import org.junit.*; 
import java.util.Arrays; 
import java.util.List; 
class IsA implements StrChecker {
    public boolean checkString(String s) { 
        return s.equalsIgnoreCase("a"); 
    }
}

public class TestListExamples { 
    
    @Test 
    public void testFilter() { 
        List<String> s1 = Arrays.asList("a", "b", "c"); 
        List<String> s2 = Arrays.asList("d", "a"); 
        
        List<String> expect = Arrays.asList("a"); 
        
        List<String> result1 = ListEx.filter(s1, new IsA()); 
        List<String> result2 = ListEx.filter(s2, new IsA()); 
        
        assertEquals(expect, result1); 
        assertEquals(expect, result2); 
    } 
    
    @Test 
    public void testFilter2() {
        List<String> s1 = Arrays.asList("a", "b", "c"); 
        List<String> s2 = Arrays.asList("d", "a", "a"); 
        
        List<String> expect1 = Arrays.asList("a"); 
        List<String> expect2 = Arrays.asList("a", "a"); 
        
        List<String> result1 = ListEx.filter(s1, new IsA());
        List<String> result2 = ListEx.filter(s2, new IsA()); 
        
        assertEquals(expect1, result1); 
        assertEquals(expect2, result2); 
    }
}
```
```ListEx.java```
```
import java.util.ArrayList;
import java.util.List;

interface StrChecker { boolean checkString(String s); } 

class ListEx {
    
    private static List<String> result = new ArrayList<>(); 
    
    static List<String> filter(List<String> list, StrChecker sc) {
        if(list.size() == 0) { 
            return list; 
        }
        result.clear();
        for(String s: list) {
            if(sc.checkString(s)) {
                result.add(s);
            }
        }
            return result;
        } 
    }
```

