# Part 1
## Failure-inducing Input
```
@Test
 public void testReversed1() {
   int[] input = {1, 2, 3};
   assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input));
}
```
## Input that doesn't induce failure
```
@Test
 public void testReversed2() {
   int[] input = { };
   assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input));
}
```
## The Bug: Before Code
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
}
```
## The Bug: After Code
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
```
# Part 2
