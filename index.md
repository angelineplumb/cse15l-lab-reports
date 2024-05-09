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




