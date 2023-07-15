# Multi-Threading
The total process is called a thread.

```
class myThread extends Thread{
// we have to override run method
public void run(){
//This is a job of thread & executed by child thread
for(i=1; i<10; i++){
sout("child thread");
}
}
}
```
```
class myThreadDemo {

// main method also is a thread 
public static void main(String[] arg){

// thread instansiation
myThread myThread = new myThread();
myThread.start(); // starting of thread
//& executed by Main thread
for(i=1; i<10; i++){
sout("child thread");
}

}
}
```

> main thread creates object thread and main thread started child thread


Case 2 ex.
```
class myThread extends Thread{
// we have to override run method
public void run(){
//This is a job of thread & executed by child thread
for(i=1; i<10; i++){
sout("child thread");
}
}
}
```

case 4:

```
class myThread extends Thread{
// this are the overloaded method
public void run(){
sout("no-arg-method");
}
public void run(int i){
sout("int arg run");
}
}
}
```

```
class myThreadDemo {


public static void main(String[] arg){
myThread myThread = new myThread();
myThread.start();
}
}
```
> o/p: no-arg run
> if you are not overloading run() Method then thread class run method will be excuted which has empty emplention heanc we want get any output

> it is highly recomemnd overide run method otherwise dont go for multithreading concept.


Case : 6 Overiding of start() method.
if you overide start method then over start() Method will be excuted just a like normal method call a new thread wont be created.

```
class myThread extends Thread{
public void start(){
sout("Start method");
}
public void run(){
sout(" run Method");
}
}
}
```
```
class myThreadDemo {
public static void main(String[] arg){
myThread myThread = new myThread();
myThread.start();
sout(" Main Method");
}
}
```
// produced by only main thread 
> O/P Start method
> Main Method

>Imp Note:  it is not recommended to overide stop method otherwise dont go for multithreading conecpt.

Case 7:
```
class myThread extends Thread{
public void start(){
super.start()
sout("Start method");
}
public void run(){
sout(" run Method");
}
}
}
```
```
class myThreadDemo {
public static void main(String[] arg){
myThread myThread = new myThread();
myThread.start();
sout(" Main Method");
}
}
```
// 3 possibality of method is there 
> O/P Start method
> Main Method
> run Method

Case 8: Thread life cycle

![Thread_Life_Cycle_(1)](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/22b13c07-2c13-42c9-b0fd-3c12db3a92e6)

Case 9: after starting a thread if you are trying to to resatrt the same thread then we will get runtime exception saying IllegalThreadstateException like we are going to get
very Imp for Interview
```
class myThreadDemo {
public static void main(String[] arg){
myThread myThread = new myThread();
myThread.start();
myThread.start();

}
}
```
Defining a thread by runnable interface 
we can defin thread by impmemnting runnable interface 

myThread ----->Thread ---->runnable()  // 1st approch
myThread ------------------->runnable() // 2nd approach

> runnable interface pregent in java.lang.*; pacakge and it content only one method(public void run())
```
class myRunnable implement thread{

// exucted by child thread
public void main(){
for(i=1; i<10; i++){
sout("main thread");
}
}
}

````



```
class threadDemo{

public static void main(string []arg)
myrunnbale r = new myrunnbale();
excuted by main method
thread t = new thread(r);
t.start
for(i=1; i<10; i++){
sout("main thread");
}
}
```


Case study:
myrunnable r = new myrunnable();
thread t1 = new thread();
thread t2 = new thread(r);


Case 1: t.start(); // a new thread will be created which is responsible for the excution of thread class runmethod(), which has emmpty emplimention
Case 2: t1.run(); // a new thread wiil not be created and thread class run methid will be excuted just like normal method call.
Case 3: t2.start(); // a new thread will be created which is responsibe for the excution of my runnable class run method
Case 4: t2.run(); // a new thread wont be created and my runnable run method will be excuted just like normal method call.
Case 5: r.start(); // we will get compile time error. saying my runnable class dosent have start cappiblity  CE: can not find symbole method stop 
Case 6: r.run(); // my runnable run method will be excuted like normal method call.

which approch is best to define a thread ->extend or implemting which one is best for thread
among two way define a thread implemtion runnabel approch is recommended in the first approch over class alwasy externs thread class, there is k=no chnace of extednig any other class henac we are messing enhetiance benifit. but in second approch while implmenting runable intrface we can extend any other class, we want any miss inherticae benifit. becous of above resone implmenting runnable interface appoch is recommended that extending thread class.



** thread class constructor 
thread t1 = new thread();
thread t2 = new thread(runnable r);
thread t3 = new thread(string name);
thread t4 = new thread(runnable r, string name);
thread t5 = new thread(ThreadGroup g, string g);
thread t6 = new thread(ThreadGroup g, runnable r);
thread t7 = new thread(ThreadGroup g, runnable r, String name);
thread t8 = new thread(ThreadGroup g, runnable r, String name, long stacsize);
> this are the verious thread constructor pregent in constructor class.


* getting and seeting name of thread
Example:
```
class myThread extends Thread{

}
class test{
public static void main(){

syste.out..println(Thread.currentThread().getName());
}
myThread t = new myThread();
syste.out..println(t.getName()); Thread-0
Thread.currentThread().setName("xyz");
Thread,currentThread().getName();
}


```
> every thread in java has some name it may be diffult name genrated by JVM and customiszed name provided by programmer
> we can get and set name of a thread by using fallowing two methods of thread class public final string getName(); public final string setName();

* Thread Object
```
class myThread extends Thread{

public void main(){

}

}
class test{
public static void main(String [] arg){

myThread t = new myThread();
t.start();

}

}
```
> we can get current thread excution object by using "Thread.currentThread().getName();"
