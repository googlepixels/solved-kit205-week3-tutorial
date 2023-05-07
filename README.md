Download Link: https://assignmentchef.com/product/solved-kit205-week3-tutorial
<br>
We will be using Microsoft Visual Studio in this unit.  You should follow the instructions below when creating a new project.

<ol>

 <li>Start Microsoft Visual Studio.</li>

 <li>Choose <em>New Project…</em> from the <em>File</em></li>

 <li>Select the <em>Visual C++</em> template and choose <em>Windows Desktop</em> then <em>Windows Desktop Wizard</em>.</li>

 <li>Enter a name for the project (e.g. <em>Week3</em>) and check the location at the bottom of the <em>New Project</em> window (you probably want to put it on your network drive in a folder for KIT205). Click <em>OK</em>.</li>

 <li>When the <em>Wizard</em> starts hit the <em>Next&gt;</em></li>

 <li>Choose <em>Empty Project</em> and uncheck <em>Precompiled Headers</em> and<em> Security Development Lifecycle (SDL) checks</em>, and click <em>Finish</em>.</li>

 <li>From the <em>Project</em> menu, choose <em>Add New Item…</em></li>

 <li>Choose a new <em>C++ File</em> and give it a name (e.g. <em>c</em>). Make sure that you change the filename extension from <em>.cpp</em> to <em>.c</em>.</li>

 <li>The new empty file should now be open. Write a simple program (that is, a <em>main</em> method) that displays “hello world” on the console.</li>

 <li>Run the program without debugging (<em>Ctrl F5</em>) so that the console window isn’t immediately closed.</li>

</ol>

<h1>Code Analysis and Profiling</h1>

In this tutorial you will calculate the O() running time of the functions below, then implement them and run tests to see if the running times match your predictions.

<ol start="11">

 <li>Analyse (theoretically) the running time of the following functions:</li>

</ol>

int f1(long n){  int k = 0;

for (int i = 0; i &lt; n; i++){

for (int j = 0; j &lt; n; j++){             k++;

}

}

return k;

}

void f2(long n){        int k = 0;

for (int i = 0; i &lt; n; i++){

for (int j = 0; j &lt; i; j++){                    k++;

}

for (int t = 0; t &lt; 10000; t++){

k++;

}

}

} void f3(long n){  if (n &gt; 0){

f3(n / 2);   f3(n / 2);

}

}

void f4(long n){

if (n &gt; 0){

f4(n / 2);   f4(n / 2);   f2(n);

}

}

void f5(long n){

int k = 0;

for (int i = 0; i &lt; 10; i++){            int j = n;            while (j &gt; 0){

k++;

j = j / 2;

}

}

}

void f6(long n){  f2(n);  f3(n);  f5(n);

}

void f7(long n){  int k = 0;

for (int i = 0; i &lt; f1(n); i++){

k++;

}

for (int j = 0; j &lt; n; j++){         k++;

}

}

Now that we have theoretical times for the functions, let’s check your predictions experimentally.

<ol start="12">

 <li>Copy your main function from last week (the one with a while loop for selecting options), but modify the while loop so that the options 1..7 select functions named f1..f7 (as defined above), calling them as <em>f1(n);</em> for example.</li>

 <li>Next, add the time header to your project:</li>

</ol>

#include &lt;time.h&gt;




<ol start="14">

 <li>In the while loop

  <ol>

   <li>Create an <em>option</em> variable and scanf into <em>option</em> as before</li>

   <li>if <em>option</em> is not equal to 0,

    <ol>

     <li>prompt for the value of <em>n</em> and set up a timer:</li>

    </ol></li>

  </ol></li>

</ol>

long n;              printf(“Enter a value for n
”);               scanf(“%d”, &amp;n);

clock_t start = clock();

<ol>

 <li>Call the appropriate function, based on <em>option</em> and pass the value for <em>n</em></li>

</ol>

<ul>

 <li>Add the following code to print the time:</li>

</ul>

clock_t diff = clock() – start;           long msec = diff * 1000 / CLOCKS_PER_SEC;      printf(“Operation took %d milliseconds

”, msec);

<ol>

 <li>else, if <em>option</em> is 0, set <em>quit</em> to 1 as before.</li>

</ol>

<ol start="15">

 <li>Now copy the functions into your project and record the times for various values of n in the spreadsheet provided. A good approach is to start with n=1 and then keep doubling the value of n until the program takes a few seconds to run.</li>

 <li>Plot the data and confirm graphically that your O() predictions were valid. You may have to scale your O() functions as per the definition of O().</li>

</ol>

Note that I didn’t include any exponential or factorial functions in this tutorial to save time, but rest assured that there are many simple functions (e.g. recursive Fibonacci) that are exponential, and problems where the <em>only</em> known solutions are exponential or factorial.