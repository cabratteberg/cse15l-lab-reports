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
## The Symptom
![Image](lab3_symptom.png)
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
The code fix of swapping the assingment from `arr[i]` to `newArray[arr.length - i - 1]` to `newArray[arr.length - i - 1]` to `arr[i]` addresses the issue because before the code was assigning the values of the original array to the values of the newArray which was all the intial value of 0 and then returning the original array. This did not give the expected output because instead of reversing the array, it set all of the array values to 0. The fixed code instead assigns the appropriate index of the new array to the index of the original array, changing the values of the new array to the reversed values of the original array and then returns the new reversed array which is the desired outcome.
# Part 2
## -c
```
camillabratteberg@Camillas-MacBook-Air technical % grep -c "planes" 911report/chapter-1.txt
16
```
In the above example, I used the `-c` command-line option for the grep command. This prints the number of lines that have a match with the string that I provide as an argument which in this case was `"planes"`. This is useful because I am able to see how many times the word "planes" appears in the provided file and I could make inferences about what information is in the text without having to read all of it.
```
camillabratteberg@Camillas-MacBook-Air technical % grep -cR "genetics" biomed
biomed/1472-6807-2-2.txt:0
biomed/1471-2350-4-3.txt:0
biomed/1471-2156-2-3.txt:0
biomed/1471-2156-3-11.txt:0

... note 832 lines omitted ...

biomed/1476-4598-1-6.txt:0
```
In the above example, I used the `-c` command-line option for the grep command. Additonally, I add an `R` to search recursively thorugh a directory. This prints the number of lines that have a match with the string that I provide as an argument which in this case was `"genetics"`. This is useful because I am able to see how many times the word "genetics' appears in the files of the `biomed` directory and locate a file that would be relevant to my interest in genetics, for example. 
## -h
```
camillabratteberg@Camillas-MacBook-Air technical % grep -h "smoking" biomed/rr37.txt
          demographic characteristics, smoking history, asthma
          no statistical differences in history of ever smoking
          smoking history was assessed using questions adapted from
          substantial proportion reported ever smoking cigarettes
          (43%), with fewer indicating current smoking (7%). The
        exposure [ 6, 38], cigarette smoking, secondhand smoke
        female gender and current smoking as risk factors for
        44]. The lack of association with smoking could be
        to this principle, persons who develop smoking-related
        respiratory symptoms quit smoking, resulting in current
        smoking.
```
In the above example, I used the `-h` command-line option for the grep command. This prints the lines that have a match with the string that I provide as an argument which in this case was `"smoking"`. This is useful because I am able to gain in insight into the relevance of smoking to the topic discussed in this text file. 
```
camillabratteberg@Camillas-MacBook-Air technical % grep -hR "Dr. Psaty" biomed
        Dr. Psaty was a Merck/SER Clinical Epidemiology Fellow
```
In the above example, I used the `-h` command-line option for the grep command. Additonally, I add an `R` to search recursively thorugh a directory. This prints the lines that have a match with the string that I provide as an argument which in this case was `"Dr. Psaty"`. This is useful because I am able to see if this directory contains any references to an author/researcher/etc. whose work I may be interested in, for example.
## -C
```
camillabratteberg@Camillas-MacBook-Air technical % grep -C 3 "parasitic" biomed/gb-2003-4-6-r39.txt
        have no obvious direct impact on humans. Others, however,
        are adapted as parasites and are responsible for such
        widespread problems as human disease, debilitation of
        livestock and crop damage. Plant-parasitic forms are
        responsible for an estimated $100 billion in annual crop
        damage worldwide [ 2 ] . The most damaging family (the
        Heteroderidae) includes the root-knot ( 
--
        leading to compromised root function and retardation of
        plant growth [ 3 ] .
        It is not clear which genetic differences between the
        plant parasitic and non-parasitic forms may be responsible
        for conferring parasitic ability. On the basis of
        phylogenetic analysis [ 4 ] it appears that plant
        parasitism arose independently at least three times over
        the course of nematode evolution. Consequently, one cannot
        be assured that any gene or set of genes that aid in the
        parasitic lifestyle in one nematode species will also exist
        in another. Conceptually, several mechanisms affecting
        evolution to parasitism can be envisioned. These include
        adaptation of pre-existing genes to encode new functions;

... note 7 instances omitted ...

--
          database, using the above parameters. The results from
          this second filter were examined and any sequence with a
          significant match to a metazoan other than a closely
          related plant-parasitic nematode was removed from further
          analysis. An e-value of 1.0e -10was the threshold used to
          declare a match. The remaining sequences provided our
          final set of candidates for horizontally transferred
```
In the above example, I used the `-C` command-line option for the grep command. This prints lines that have a match with the string that I provide as an argument which in this case was `"parasitic"` and a certain number of lines before and after provided as an argument which in this case was 3. This would be useful if you want to find information about a specific topic and want context around the instance, not just one line.
```
camillabratteberg@Camillas-MacBook-Air technical % grep -C 2 "Chile" plos/journal.pbio.0020001.txt
        Among Latin American countries, there is a high degree of variability in publication
        rate as well as in financial investment in science and technology. Some countries have
        performed particularly well. For example, Uruguay, Chile, Panama, and Cuba averaged,
        respectively, 6.8, 5.3, 5.2, and 3.4 publications per million dollars of research and
        development investment in the 10 years studied, which is notoriously high compared with
        United States (1.5) and even Canada (3.3) (RICYT 2002). Other countries, such as Costa
        Rica, Cuba, Brazil, and Chile, have invested a much greater proportion of their GDP in
        research and development than the other countries of this region (Albornoz 2001).
```
In the above example, I used the `-C` command-line option for the grep command. This prints lines that have a match with the string that I provide as an argument which in this case was `"Chile"` and a certain number of lines before and after provided as an argument which in this case was 2. This is useful because I am able to quickly find information about Chile in the text file. 

## -n
```
camillabratteberg@Camillas-MacBook-Air technical % grep -n "Longabaugh" government/Alcohol_Problems/DraftRecom-PDF.txt
78:Richard Longabaugh said that the term "alcohol problems" implies
116:Longabaugh wondered whether the intended consumers of the
230:Longabaugh noted that new and creative interventions may be
441:Longabaugh wanted the recommendation to include research
493:Longabaugh commented that an NIAAA effort to conduct research on
547:Longabaugh remarked that NIH is increasingly trying to
```
In the above example, I used the `-n` command-line option for the grep command. This prints lines that have a match with the string that I provide as an argument which in this case was the name "Longabaugh" and the corresponding line number. This is useful if you want to find instances of a certain phrase and which lines they are used in so you would know where in the file to look to find more information.
```
camillabratteberg@Camillas-MacBook-Air technical % grep -nR "drugs" 911report
911report/chapter-3.txt:134:                traditional crimes such as white-collar offenses and those pertaining to drugs and
911report/chapter-3.txt:1253:                (a portfolio often known as "drugs and thugs"), the veteran civil servant Richard
911report/chapter-6.txt:1649:                back to the investigative basics: guns, drugs, and civil rights. The new
911report/chapter-12.txt:930:                concern about the "war on drugs," the right level and kind of immigration, problems
```
In the above example, I used the `-n` command. Additonally, I add an `R` to search recursively thorugh a directory. This prints lines that have a match with the string that I provide as an arguement which in this case was `"drugs"`, the corresponding line number and the file in which the line was found in. This is useful if you are trying to find information about a certain topic in a directory and you want to find files and specific parts of files that are relevant to your goals.

Source (for all): https://www.geeksforgeeks.org/grep-command-in-unixlinux/
