# Lab Report 9

## Student Post

Hi everyone,
I am working on a filter method that is used to extract a certain string from an array list. My first test works correctly, 
but on my second tests, I do not get the expected output.

```TestExamples.java```
```import static org.junit.Assert.*; 
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
