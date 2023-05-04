Download Link: https://assignmentchef.com/product/solved-csci-1301-lab-12-more-on-classes-objects-and-methods
<br>
<h1>Introduction</h1>

This lab focuses on method overloading and also gives you further practice working with some subtleties of one-dimensional arrays. In it, you will modify the <strong>Stat</strong> class created in the previous lab, expanding its functionality. If you recall, that class stored an array of <strong>double</strong> values and computed the minimum, maximum, mode, and average of these values. There were also methods for getting and setting the array of values. In particular, there was a method called <strong>setData</strong> which used a <strong>double</strong> array as its single parameter, and it copied the values from that array to the underlying data array of the <strong>Stat</strong> object.




In this lab, you will overload the <strong>setData</strong>  method (and the class constructors as well), creating versions that use arrays of <strong>int</strong>, <strong>long</strong>, and <strong>float</strong> values as parameters and handles <strong>null</strong> parameters properly (i.e. runtime errors should not occur when a parameter is <strong>null</strong>). A <strong>double</strong> array will still be used internally by the <strong>Stat</strong> class to store the values.  You will also define an additional set of methods, all called <strong>append</strong>, to add new values to the underlying data array.







<h2>Important note about this lab</h2>

If you completed the previous <strong>Stat</strong> lab, then you may reuse your own source code from that lab for this lab. However, if you did <strong><em>NOT</em></strong> complete the previous <strong>Stat</strong> lab, then you will need to do additional work to complete all of the methods in this lab. Source code from the previous <strong>Stat</strong> lab will <strong><em>NOT</em></strong> be provided, and you are <strong><em>NOT</em></strong> permitted to ask other students for any code associated with this lab or the previous <strong>Stat</strong> lab.  Also, you are <strong><em>NOT</em></strong> permitted to give source code to other students for this lab or the previous <strong>Stat</strong> lab.  <strong> </strong>




It is important to note that the automatic type conversion of primitive data types that can occur during method calls does not apply to arrays of primitive data types. And so, while it is perfectly possible to define a method having formal parameters that are <strong>double</strong> values and then invoke that method using <strong>int</strong> values, it is not possible to automatically convert, for instance, an <strong>int</strong> array to a <strong>double</strong> array.  Automatic type conversion can be performed on individual elements of arrays but not on the arrays themselves.




In the lab, you will also modify the code of the <strong>Stat</strong> class to allow a data array of 0 elements. It is perfectly possible to create an array of length 0 in Java, and having a variable hold a reference to an array of length 0 is in many ways preferable to simply assigning <strong>null</strong> to the variable (it avoids so-called null pointer exceptions, for instance).




Using zero-length arrays requires altering the methods of the <strong>Stat</strong> class that were defined in the previous lab. E.g., an empty array has no minimum or maximum value, and so we modify the methods <strong>min</strong> and <strong>max</strong> to return <strong>Double.NaN</strong>  (which represents “Not a Number”) in those cases. Other adjustments in the same vein are needed throughout the modified program.




The class will also be modified in this lab to handle methods invoked with <strong>null</strong> as a parameter.  Specifically, you will need to modify several of the methods to check that the value passed to them is not <strong>null</strong>. In part, this is done to ensure that calculations are never performed on null values (this makes your program more robust).




As part of the lab, you will also implement methods to compute the variance and standard deviation of the stored data values.

<strong> </strong>

It is important to note that if done somewhat naively, your finished program might contain a significant amount of redundant code. Such redundancy should in general be avoided, as it is ultimately more difficult to maintain, and it increases the chances of an error occurring in your program. Because of this, you should attempt to identify tasks in your program that need to be performed often and then defining a method to perform that task. Once done, other methods can be implemented to make use of it.

<strong> </strong>

<h1>Lab Objectives</h1>

By the end of the lab, you should be able to create classes utilizing:  constructors; access modifiers; instance variables; void methods and methods which return values; accessor and mutator methods (getters and setters) methods; methods calling other methods; method overloading.

You should have also gained further experience working with one-dimensional arrays (including empty arrays) of various data types.

<strong>Prerequisites </strong>

The lab deals with material from Chapter 5, 6, and 7.

<h1>What to Submit</h1>

The modified <strong>Stat.java</strong> file should be submitted to eLC for grading (you should keep a copy of the original).

<h1>Instructions</h1>

Use the UML diagram and method descriptions below to create your modified <strong>Stat</strong> class. In the diagram, methods not defined in the previous lab are shown in red. Observe that in many cases, previously existing methods require alteration.




<table width="487">

 <tbody>

  <tr>

   <td colspan="2" width="487"><strong>                         Stat </strong></td>

  </tr>

  <tr>

   <td colspan="2" width="487"><strong> </strong><strong>– data: double[] </strong><strong> </strong></td>

  </tr>

  <tr>

   <td colspan="2" width="487"><strong> </strong><strong>1.      </strong><strong>+ Stat() </strong><strong>2.      </strong><strong>+ Stat(double[] d) </strong><strong>3.      </strong><strong>+ Stat(float[] f) 4.</strong> <strong>+ Stat(int[] i) </strong><strong>5.      </strong><strong>+ Stat(long[] lo) </strong><strong>6.      </strong><strong>+ setData(float[] f): void </strong><strong>7.      </strong><strong>+ setData(double[] d): void </strong><strong>8.      </strong><strong>+ setData(int[] i): void </strong><strong>9.      </strong><strong>+ setData(long[] lo): void </strong><strong>10.     </strong><strong>+ getData(): double[] </strong><strong>11.     </strong><strong>+ equals(Stat s): boolean </strong><strong>12.     </strong><strong>+ reset(): void </strong><strong>13.     </strong><strong>+ append(int[] i): void </strong><strong>14.     </strong><strong>+ append(float[] f): void </strong><strong>15.     </strong><strong>+ append(long[] lo): void </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>16.</strong></td>

   <td width="432"><strong>+ append(double[] d): void </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>17.</strong></td>

   <td width="432"><strong>+ isEmpty(): boolean </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>18.</strong></td>

   <td width="432"><strong>+ toString(): String </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>19.</strong></td>

   <td width="432"><strong>+ min(): double </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>20.</strong></td>

   <td width="432"><strong>+ max(): double </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>21.</strong></td>

   <td width="432"><strong>+ average(): double </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>22.</strong></td>

   <td width="432"><strong>+ mode(): double </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>23.</strong></td>

   <td width="432"><strong>– occursNumberOfTimes(double value): int </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>24.</strong></td>

   <td width="432"><strong>+ variance(): double </strong></td>

  </tr>

  <tr>

   <td width="55"><strong>25.</strong></td>

   <td width="432"><strong>+ standardDeviation(): double </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong><u>In your code, you are not allowed to use any java.util.Arrays methods or the java stream</u></strong><strong> <u>API (if you are familiar with either of these).  Using the java.util.Arrays class or Java</u> <u>stream in any way will result in a grade of zero on this assignment.</u> </strong><strong>  </strong>

<strong> </strong>

<strong>Method Descriptions: </strong>

<ul>

 <li><strong>(1) Stat()</strong><strong>—</strong>The default constructor for <strong>Stat</strong>. It should create a <strong>double</strong> array having length 0.</li>

</ul>

<h2>• (2,3,4,5) Stat(double[] d), Stat(int[] i), Stat(long[] lo),</h2>

<strong>Stat(float[] f)</strong><strong> —</strong> Constructs a <strong>Stat</strong> object using the values held in the parameter array.  Invoking the constructor should create a <strong>double</strong> array of the same length as the parameter array and holding copies of its values. A reference to this new array should be assigned to <strong>data</strong>.

Note that if the parameter is <strong>null</strong>, then an empty array should instead be assigned to <strong>data</strong>.

<ul>

 <li><strong>(6,7,8,9) setData(double[] d)</strong>, <strong>setData(int[] i)</strong>, <strong>setData(long[] lo)</strong>, <strong>setData(float[] f)</strong><strong> —</strong> As in the previous lab, these methods are used to set the values of the <strong>data</strong> Here, if the array used as parameter is not <strong>null</strong>, then each of these methods should create a new <strong>double</strong> array containing exactly the elements of the parameter array. A reference to this new array is assigned to<strong> data</strong>. If the parameter is <strong>null</strong>, however, then an empty array should instead be assigned to <strong>data</strong>.</li>

 <li><strong>(10) getData()</strong><strong>—</strong>This method is left unchanged from the previous lab. It should create a new array containing exactly the values contained in <strong>data</strong> and return a reference to this new array. This should happen even if <strong>data</strong> is an empty array (has length 0).</li>

 <li><strong>(11) equals(Stat s)</strong><strong> —</strong> Unchanged from the previous lab. The method returns <strong>true</strong> if the <strong>data</strong> arrays of both objects, the calling <strong>Stat</strong> object and the passed <strong>Stat</strong> object <strong>s,</strong> have the same values (and in the same order). Otherwise, it returns <strong>false</strong>. If the parameter <strong>s</strong> is null, the method returns <strong>false</strong>.</li>

 <li><strong>(12) reset()</strong>: This clears the data array. A new empty <strong>double</strong> array is created and assigned to <strong>data</strong>.</li>

 <li><strong>(13,14,15,16) append(double[] d)</strong>, <strong>append(int[] i)</strong>, <strong>append(long[] lo)</strong>, <strong>append(float[] f)</strong><strong> —</strong>These methods should create a new double array containing exactly those elements of <strong>data</strong> followed by those of the array passed as parameter. A reference to this array should be assigned to <strong>data</strong>. If the parameter is <strong>null</strong>, then the method should do nothing (no new array created).</li>

 <li><strong>(17) isEmpty()</strong><strong>—</strong> returns the <strong>boolean</strong> value <strong>true</strong> if the <strong>data</strong> object is empty (has length 0). Otherwise, it returns <strong>false</strong>.</li>

 <li><strong>(18) toString()</strong><strong>—</strong>As in the previous lab, this method returns a <strong>String</strong> representation of the data elements, if any, stored in the <strong>Stat</strong> See the examples below for the correct format.</li>

 <li><strong>(19) min()</strong><strong>—</strong>Returns the minimum of the <strong>data </strong> If the array is empty, then it should return <strong>Double.NaN</strong>.</li>

 <li><strong>(20) max()</strong><strong>—</strong>Returns the maximum of the <strong>data </strong> If the array is empty, then it should return <strong>Double.NaN</strong>.</li>

 <li><strong>(21) average()</strong><strong>—</strong>Returns the average or mean of the values in the <strong>data </strong> If <strong>data </strong>is an empty array, then the method should return <strong>Double.NaN</strong>.</li>

 <li><strong>(22) mode()</strong>— The mode is the value that occurs most frequently in a collection of values. In the <strong>Stat</strong> class, if one value occurs more frequently in <strong>data</strong> than all others, then <strong>mode()</strong> should return this value. If there is no such unique value, or if the data array is empty, <strong>mode() </strong>should return <strong>NaN</strong>.</li>

 <li><strong>(23) occursNumberOfTimes(double value)</strong> — Returns the number of times the <strong>value</strong> occurs in the <strong>data</strong> This is a private helper method for the <strong>mode() </strong>method, and its implementation is optional, but excellent practice decomposing the <strong>mode() </strong>method.</li>

 <li><strong>(24) variance()</strong>— Returns the variance of the data in the <strong>data </strong> To compute this, find the difference between the value of each element of the data array and the mean, square this distance, and then sum these squared values. The variance is this sum divided by the number of elements in <strong>data</strong>.</li>

</ul>

Note that if the <strong>data</strong> array is empty, then <strong>Double.NaN</strong> should be returned.

<ul>

 <li><strong>(25) standardDeviation(): </strong>Returns the square root of the variance. If the <strong>data</strong> array is empty, then  <strong>NaN</strong> should be returned.</li>

</ul>




<h1>Additional Requirements</h1>

These are things that make the graders lives easier, and ultimately, you will see in the real world as well. Remember the teaching staff does not want to touch your code after they gave you requirements; they want to see the perfect results they asked for! Here is a checklist of things you can<strong> lose points</strong> for:




<ul>

 <li>(-10 points) If the source file(s)/class(es) are named incorrectly (case matters!)</li>

 <li>(-10 points) If your source file(s) have a package declaration at the top</li>

 <li>(-10 points) If any source file you submit is missing your Statement of Academic Honesty at the top of the source file. All submitted source code files must contain your Statement of Academic Honesty at the top of each file.</li>

 <li>(-10 points) If you have more than one instance of Scanner in your program.</li>

 <li>(-15 points) Inconsistent I/O (input/output) that does not match our instructions or examples exactly (unless otherwise stated in an assignment’s instructions). Your program’s I/O (order, wording, formatting, etc.) must match our examples and instructions.</li>

 <li>(-100 points) If the source file(s) are not submitted before the specified deadline’s late period ends (48 hours after the deadline) or if they do not compile.</li>

 <li>(-25 points) Late penalties will be deducted as per the course syllabus.</li>

 <li>If your (-10 points) comments or (-10 points) variables are “lacking” o Here, “lacking” means that you or a TA can find <strong>any</strong> lines of code or variables that take more than 10 seconds to understand, and there is no comment, or the variable name does not make sense (variable names like <strong>b</strong>, <strong>bb</strong>, <strong>bbb</strong>, etc. <strong>will</strong> <strong>almost never be acceptable) </strong></li>

 <li>(-10 points) Indentation is not consistent throughout your source code o Refresh your memory of indentation patterns in chapter 2 in the course textbook o Be careful of a combination of tabs and spaces in your files (use one or the other)!</li>

 <li>(-100 points) If you use a non-standard Java library or class (StringBuilder class, Arrays class, any class in java.util.stream) or other code specifically disallowed by the lab/project.</li>

</ul>

If any of the above do not make sense to you, then talk to a TA or your lab instructor. <strong>eLC Submission and Grading </strong>

After you have completed and thoroughly tested your program, upload <strong>Stat.java</strong> to <strong><em>eLC</em></strong> to receive credit. Always double check that your submission was successful on <strong><em>eLC</em></strong>!  All instructions and requirements must be followed; otherwise, points maybe deducted.

<h1>Examples</h1>

<em> </em>

<h2>Example 1</h2>




<em><u>Example main method:</u></em>

<em> </em>

<strong>double</strong>[] data1 = {}; Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation()); System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”);







<em><u>Example output:</u></em>

stat1 data = [] stat1 min = NaN stat1 max = NaN stat1 average = NaN stat1 mode = NaN stat1 variance = NaN stat1 standard deviation = NaN stat1 is empty = true

<strong> </strong>

<h2>Example 2</h2>




<em><u>Example main method:</u></em>

<em> </em>

<strong>double</strong>[] data1 = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation()); System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”);




stat1.reset();

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation()); System.<em>out</em>.println(“stat1 is empty = ” + stat1.isEmpty() + “
”);







<em><u>Example output:</u></em>




stat1 data = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0] stat1 min = 1.0 stat1 max = 9.0 stat1 average = 5.0 stat1 mode = NaN

stat1 variance = 6.666666666666667 stat1 standard deviation = 2.581988897471611 stat1 is empty = false

stat1 data = [] stat1 min = NaN stat1 max = NaN stat1 average = NaN stat1 mode = NaN stat1 variance = NaN stat1 standard deviation = NaN stat1 is empty = true

<h2>Example 3</h2>




<em><u>Example main method:</u></em>




<strong>float</strong>[] data1 = {10.0F,10.0F};

Stat stat1 = <strong>new</strong> Stat(data1);

System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”); <strong>long</strong>[] data2 = {80L, 60L};




stat1.append(data2);




System.<em>out</em>.println(“stat1 data = ” + stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);

<em><u>Example output:</u></em>




stat1 data = [10.0, 10.0] stat1 min = 10.0 stat1 max = 10.0 stat1 average = 10.0 stat1 mode = 10.0 stat1 variance = 0.0

stat1 standard deviation = 0.0




stat1 data = [10.0, 10.0, 80.0, 60.0] stat1 min = 10.0 stat1 max = 80.0 stat1 average = 40.0 stat1 mode = 10.0 stat1 variance = 950.0

stat1 standard deviation = 30.822070014844883

<h2>Example 4</h2>




<em><u>Example main method:</u></em>

<em> </em>

<strong>double</strong>[] data = {-5.3, 2.5, 88.9, 0, 0.0, 28, 16.5, 88.9, 109.5, -90, 88.9};

Stat stat1 = <strong>new</strong> Stat();




System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());




stat1.append(data);




System.<em>out</em>.println(“stat1 has been altered.”);




System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);

<em><u>Example output:</u></em>

stat1 data = [] stat1 has been altered. stat1 data = [-5.3, 2.5, 88.9, 0.0, 0.0, 28.0, 16.5, 88.9, 109.5, -90.0, 88.9] stat1 min = -90.0 stat1 max = 109.5

stat1 average = 29.80909090909091 stat1 mode = 88.9

stat1 variance = 3192.369917355372 stat1 standard deviation = 56.50106120556827

<h2>Example 5</h2>




<em><u>Example main method:</u></em>

<em> </em>

<strong>double</strong>[] data1 = {50.0, 60.0}; <strong>float</strong>[]  data2 = {70.0F, 80.0F}; <strong>int</strong>[]    data3 = {90, 100};

<strong>long</strong>[]    data4 = {100L, 110L};




Stat stat1 = <strong>new</strong> Stat();

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());                 stat1.setData(data1);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.setData(data2);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.setData(data3);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.setData(data4);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); data1 = <strong>null</strong>; stat1.setData(data1);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());

<em><u>Example output:</u></em>




stat1 data = [] stat1 data = [50.0, 60.0] stat1 data = [70.0, 80.0] stat1 data = [90.0, 100.0] stat1 data = [100.0, 110.0] stat1 data = []

<h2>Example 6</h2>




<em><u>Example main method:</u></em>

<em> </em>

<strong>double</strong>[] data1 = {50.0, 60.0}; <strong>float</strong>[]  data2 = {70.0F, 80.0F}; <strong>int</strong>[]    data3 = {90, 100}; <strong>long</strong>[]    data4 = {100L, 110L};

Stat stat1 = <strong>new</strong> Stat();

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());

stat1.append(data1);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.append(data2);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.append(data3);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); stat1.append(data4);

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString()); data1 = <strong>null</strong>; stat1.append(data1);




System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());

System.<em>out</em>.println(“stat1 min = ” + stat1.min());

System.<em>out</em>.println(“stat1 max = ” + stat1.max());

System.<em>out</em>.println(“stat1 average = ” + stat1.average()); System.<em>out</em>.println(“stat1 mode = ” + stat1.mode());

System.<em>out</em>.println(“stat1 variance = ” + stat1.variance());

System.<em>out</em>.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);

<em><u>Example output:</u></em>




stat1 data = [] stat1 data = [50.0, 60.0] stat1 data = [50.0, 60.0, 70.0, 80.0] stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0]

stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0, 100.0, 110.0] stat1 data = [50.0, 60.0, 70.0, 80.0, 90.0, 100.0, 100.0, 110.0] stat1 min = 50.0 stat1 max = 110.0 stat1 average = 82.5 stat1 mode = 100.0 stat1 variance = 393.75

stat1 standard deviation = 19.84313483298443

<h2>Example 7</h2>




<em><u>Example main method:</u></em>

<strong> double</strong>[] data1 = {10,10}; <strong>int</strong>[] data2 = {10,10}; Stat stat1 = <strong>new</strong> Stat(data1);

Stat stat2 = <strong>new</strong> Stat(data2);

Stat stat3 = <strong>new</strong> Stat();

Stat stat4 = <strong>null</strong>;

System.<em>out</em>.println(“stat1 data = ” +  stat1.toString());

System.<em>out</em>.println(“stat2 data = ” +  stat2.toString());

System.<em>out</em>.println(“stat2 data = ” +  stat2.toString());

System.<em>out</em>.println(“stat1 equals stat2 = ” +  stat1.equals(stat2));

System.<em>out</em>.println(“stat1 equals stat3 = ” +  stat1.equals(stat3));

System.<em>out</em>.println(“stat1 equals stat4 = ” +  stat1.equals(stat4));

<em><u>Example output:</u></em>

stat1 data = [10.0, 10.0] stat2 data = [10.0, 10.0] stat2 data = [10.0, 10.0] stat1 equals stat2 = true stat1 equals stat3 = false stat1 equals stat4 = false




<h2>Example 8</h2>




<em><u>Example main method:</u></em>

<strong> double</strong>[] data1 = {}; <strong>double</strong>[] data2 = { 25 }; <strong>float</strong>[] data3 = {}; <strong>float</strong>[] data4 = { 25 }; <strong>int</strong>[] data5 = {}; <strong>int</strong>[] data6 = { 50 }; <strong>long</strong>[] data7 = {}; <strong>long</strong>[] data8 = { 12 };




Stat stat1 = <strong>new</strong> Stat(); stat1.append(data1); stat1.append(data2); stat1.append(data3); stat1.append(data4); stat1.append(data5); stat1.append(data6); stat1.append(data7); stat1.append(data8); data1 = <strong>null</strong>; stat1.append(data1);




System.out.println(“stat1 data = ” + stat1.toString());

System.out.println(“stat1 min = ” + stat1.min());

System.out.println(“stat1 max = ” + stat1.max());

System.out.println(“stat1 average = ” + stat1.average()); System.out.println(“stat1 mode = ” + stat1.mode());

System.out.println(“stat1 variance = ” + stat1.variance());

System.out.println(“stat1 standard deviation = ” + stat1.standardDeviation() + “
”);

<em><u>Example output:</u></em>

stat1 data = [25.0, 25.0, 50.0, 12.0] stat1 min = 12.0 stat1 max = 50.0 stat1 average = 28.0 stat1 mode = 25.0 stat1 variance = 189.5

stat1 standard deviation = 13.765899897936205













<h2>Lab 12 – More on Classes, Objects, and Methods</h2>




Copyright © Sal LaMarca and the University of Georgia. This work is licensed under a <a href="https://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International</a> <a href="https://creativecommons.org/licenses/by-nc-nd/4.0/">License</a> to students and the public. The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.S