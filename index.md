# Part 1<br>
## Faliure inducing input for averageWithoutLowest <br>

```
@Test
  public void testAverageWithoutLowest() {
    double[] input2 = { 1, 2, 1, 3, 4};
    assertEquals(2.5, ArrayExamples.averageWithoutLowest(input2), 0);
  }
```
## Input that doesn't cause error for averageWithoutLowest <br>
```
@Test
  public void testAverageWithoutLowest() {
    double[] input1 = { 1 };
    assertEquals(0.0, ArrayExamples.averageWithoutLowest(input1), 0);
    double[] input2 = { 1, 2, 3, 4};
    assertEquals(3, ArrayExamples.averageWithoutLowest(input2), 0);
  }
```
## Output of running tests for averageWithoutLowest <br>
![Image](testimage.png) <br>
## Code for averageWithoutLowest before change<br>
```
 static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```
## Code for averageWithoutLowest after change<br>
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    int index = 0;
    for(int i = 0; i < arr.length; i++) {
      if(arr[i] < lowest) { lowest = arr[i]; index = i;}
    }
    double sum = 0;
    for(int i = 0; i < arr.length; i++) {
      if(i != index) { sum += arr[i]; }
    }
    return sum / (arr.length - 1);
  }
```
This fixes the issue because instead of skipping all numbers in the array that equal to lowest, we take the index of the lowest and skip that. This way only one index is being skipped and not every instance of the lowest number. 

# Part 2<br>
## grep -v
```
angie@Angies-MacBook-Air-2 technical % grep -v "e" biomed/rr74.txt

  
    
      
        Introduction
        pulmonary vasoconstriction. Chronic NOS inhibition did not
        NO is important in modulating basal pulmonary vascular
      
      
        
        
        
        
        
        
        
          antirabbit (nNOS, iNOS, and β-actin) for 45 min at 37°C.
        
        
          with A 
          260 /A 
          RNA.
        
        
          dilution; nNOS, Transduction N32030, 1:500 dilution),
        
        
          2 -, NO 
        
        
          Statistical analysis
          statistically significant.
        
      
      
        
          P < 0.001).
        
        
          brain).
        
        
          3.5-fold (Fig. 3).
        
        
          shown).
        
        
        
      
      
        Discussion
        21].
        circulation.
        production of NO 
        hypoxia in rats, Sato 
        in vitro and 
      
      
        Conclusion
```
```
angie@Angies-MacBook-Air-2 technical % grep -v "a" biomed/rr74.txt

  
    
      
        Introduction
        immunohistochemistry.
      
      
        
          Mice
        
        
          Exposure environments
        
        
        
        
          Western blotting
        
        
          with A 
          260 /A 
          diluted in depC H 
          determined using 18 S rRNA primers/probes (Applied
          RNA.
        
        
          Immunohistochemistry
        
        
          2 -, NO 
          (Ionics Instrument Business Group, Boulder, CO, USA).
        
        
          P < 0.05 is considered
        
      
      
        Results
        
          respectively; 
          P < 0.001).
        
        
          Western blotting
          As shown in Fig. 2, lung eNOS protein levels were
        
        
          3.5-fold (Fig. 3).
        
        
          Immunohistochemistry
          shown).
        
        
        
      
      
        Discussion
        development.
        21].
        detection in the lungs of hypoxic, hypertensive mice.
        flushed with 10% O 
        different species in cultures [ 31, 32, 33, 34, 35, 36, 37]
        production of NO 
        piglets 
      
      
        Conclusion
        considering studies using NOS-deficient mice. The present
```
The grep -v command allows us to find all text that *does not* include the given input. In these examples, I am showing all of the lines in the file "./technical/biomed/rr74.txt" where "e" and "a" do not occur. This is useful when trying to sort through text. 





