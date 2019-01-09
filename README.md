# Assignment 0
## AutoTest Dry-Run

---

AutoTest is a relatively new system developed at UBC for automatically grading coding assignments. Before you use it 
for an assignment or lab that counts towards your grade in the course, we want to provide you with an opportunity 
to try it out and make sure you understand how it works.

Please carefully follow through the steps below and check that you obtain the expected feedback from AutoTest. If 
you encounter any discrepancies, please send e-mail to pcarter@cs.ubc.ca and include a link to the page on GitHub 
that contains the unexpected feedback from AutoTest.

Clone the repository `assign0_teamxxx` (where xxx is a number) from GitHub.ugrad.cs.ubc.ca and open the project in 
IntelliJ. Although the project name contains the word "team", you will be working in a team of 1 this term - so 
think of this as a repository that is unique to you. Be sure to switch to Packages view for a simplified view 
of the project. Expand the `test` package, right-click `CustomerCounterTest` and choose "Run `CustomerCounterTest`" from the 
pop-up menu. The first time you do this, you may get an error - if so, just try to run the tests again. Notice that two 
tests run and they both pass.

Add a class-level comment to the `CustomerCounterTest` to indicate that this class contains unit tests for 
`CustomerCounter` class as follows:

```java
    // Unit tests for the CustomerCounter class
    class  CustomerCounterTest { 
```
  
You're now going to commit this change to your local repository and push the change to GitHub. To do this, select 
Commit from the VCS menu in IntelliJ. Enter a comment to describe the change you have made, something like "Added 
class-level comment to `CustomerCounterTest`", hover over the "Commit" button and select "Commit & Push" from the 
pop-up menu. Another dialog will pop-up - click the "Push" button.

Select View -> Tool Windows -> Version Control. Click the Log tab and notice that the comment that you just entered 
on your commit appears at the top of the list. Right-click the comment and choose "Open on GitHub". A web browser 
will open that shows the commit that you just pushed to GitHub. Look for a comment box towards the end of the page 
and enter:

`@autobot #assign0`

This requests AutoTest to return a grade to you. Eventually (the wait time will depend on the number of other students 
using AutoTest at the same time), another comment will be generated that contains your score from AutoTest - you may 
need to refresh the page to see it. 

You should expect to receive feedback equivalent to:

`Your code failed the checkstyle test`

Every time you request a grade from AutoTest, it will check that your code adheres to various style guidelines.  We'll
give you more information about these with your first assignment.  Rather than leaving it to AutoTest to 
check your code, you can do it yourself from within IntelliJ.  Select View -> Tool Windows -> Checkstyle.  Hover over
the buttons on the left hand side of the checkstyle window and wait for a tool tip to show up that describes what the 
button does.  Click the button labelled "Check project".  An error will be identified on line 23 of the `CustomerCounter` 
class:

`if construct must use '{};s`

Insert the braces as shown here:

```java
        if (nextCustomer >= MAX_CUSTOMER_NUMBER) {
            nextCustomer = 1;
        }
```

then re-run the checkstyle test on the project and check that no errors are reported.  Commit your code using a comment 
like "Fixed checkstyle error in CustomerCounter.nextCustomer" and push it to GitHub, as described above.  Open the 
commit on GitHub and request a grade, also as described above.  You should now expect to see an overall score of 
54.8%, a test summary score of 33.3% and a code coverage score of 76.2%. The overall score is a combination of the 
test and code coverage scores (equally weighted for this particular submission). The code coverage score is a measure 
of the degree to which the tests cover the code in the `CustomerCounter` class.  Your comment will also include a 
link to a code coverage report.  Click the link and explore the report by clicking the links in the Element column.  
Eventually you will reach a colour-coded version of your code.  Green indicates that the code was covered 
by the tests, red that it wasn't covered and yellow that it was partially covered.  

Open the `CustomerCounterTest` class and notice that one of the test methods is commented out. Uncomment this test and 
run the tests again. The test that you just uncommented will fail.

Commit and push your code to GitHub and be sure to enter a comment that describes at a high level the change that 
you made to the code. Open your commit on GitHub and request a grade from AutoTest (as described above). You should 
now expect to see an overall score of 66.7%, a test summary score of 33.3% and a 
code coverage score of 100%. So, the additional test that we are running, although it fails, serves to increase code 
coverage - it executes a part of the code that is not covered by the other tests.  Investigate the code coverage report
again and note that all of the code in `CustomerCounter` is now highlighted in green.  Also note that as part of 
the feedback from AutoTest, you have been given a hint about the failing test: 

"CustomerCounter.nextCustomer: test that customer does not exceed maximum number"

This tells you that we ran a test against the method `CustomerCounter.nextCustomer` which failed - specifically, 
we were testing that the customer number does not exceed the maximum. This gives you a hint as to where to look for 
the problem.

As noted above, the test that you uncommented in `CustomerCounterTest` failed. This is due to a bug in the `CustomerCounter` 
class. Fix the bug, run all the tests again and make sure that they pass. Once you've done this, commit and push your 
code to GitHub one last time and request another grade from AutoTest. You should now expect to see an overall score of 
100%, a test summary score of 100% and a code coverage score of 100%.

Now let's introduce a syntax error and see what kind of feedback we get from AutoTest.  Open `CustomerCounter`
and delete the semi-colon from the end of the following statement in the `nextCustomer` method:

`nextCustomer++;`

Commit and push your code to GitHub and request a grade from AutoTest.  You should receive feedback similar to:

```shell
/= /tmp/java-project/student-build/src/main/ca/ubc/cpsc210/nowserving/model/CustomerCounter.java:22: error: ';' expected
        nextCustomer++
                      ^
1 error
```

Note that the line number reported at the end of `CustomerCounter.java` (22 in this case) might be different.  Also
note that this error message is particularly helpful and that the ^ points to exactly the point in the code where 
the error occurred.  You'll likely find that not all error messages are quite as helpful - feel free to post a message
on Discourse or ask for help at a lab if you have difficulty interpreting feedback from AutoTest.

Finally, fix the syntax error you just introduced into the code.  Commit and push your code to GitHub and request 
another grade from AutoTest.  You should now be back to a score of 100%.

