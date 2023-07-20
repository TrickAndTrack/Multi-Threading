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
> We can get the current thread execution object by using "Thread.currentThread().getName();"

# Thread priority 
every thread in Java has some priority it may be diffult priority generated by JVM or customized priority provided by the programmer the valid reange of thread priority is 1 to 10 where,
1 is min_priority
10 is max_priortiy 
thread class defines the following constants to represent some standard priority Thread.min_priority =1, Thread.norm_priority=5, Thread.max_priority=10.

Thread scheduler will use priority while allocating processes the thread which is having highest priority will get a chance first

If two threads have the same priority then we can't expect the exact executing order it depends on the thread schedule.

Thread class defines the following methods to get and set a priority of the thread 
Example
public final int getpriority()
public final void setpriority(int i)

##### default priority
The default priority only for the main thread is 5 but for all remaining threads default priority will be inherited from parent to child that is whatever priority the parent thread has the same priority will be there for the child thread 
Examples:
> Note: Some platforms won't provide proper support for thread priorities.

# Preventing thread from execution
we can prevent a thread execution by using the following methods
1) yield()
2) join()
3) sleep()

1) yield() -> method causes to pause current executing thread to give a chance for the waiting thread for the same priority if there is no waiting thread are all waiting threads have low priority then the same thread can continue its execution.
if multiple threads are waiting with the same priority then which waiting thread will get a chance we can't expect it depending on the thread scheduler.
The thread which yield when it will get a chance once again depends on the thread scheduler and we can't expect it exactly.  
Example: public static native void yield(){}

![Yeild_proccess](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/03ec62ec-3f0c-49ef-b10e-63781edfdf8b)

```
class myThread extends Thread{

public void run(){

for(i=1; i<10; i++){
sout("child thread");
Thread.yield();
}
}
}

class yieldDemo{
public static void main(String [] arg){

myThread t = new myThread();
t.start();
for(i=1; i<10; i++){
sout("child thread");
}
}
}
```
in the above program if you commenting line one then both thread will execute similtencly and we can't expect which thread will complete first.
if we are not commenting on line one then child thread is always called yield method because of that main thread will get chance more number of time and chance of completing main thread first is high.

>Note: Some platforms won't provide proper support for the yield method.

2) join() -> if thread wants a wait until completing some other thread then we should go for the join method.
   ex: if t1 want to wait until completing t2 then t1 has to call t2.join(); if t1 execute t2.join() then emeidetly t1 will enter in wating sate untill t2 complete onec t2 compelte then t1 can continue its excution.

Example: ![join_method](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/72421e99-8b96-47f0-abea-28e24d6c8bc1)

public final void join() throws interaptedException;
public final void join(long ms) throws interaptedException;
public final void join(long ms, int ns) throws interaptedException;

> Note: every join method throws an interpretedexception which is a checked exception hence compulsory we should handle it either by using the try-catch or throws keyword other wise e will get compile time error.
![join_method_in_life_cycle](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/c2c03256-278c-45ab-b9a0-d95cd3aaa8a3)

if thread shedular allocates processor
```
class myThread extends Thread{

public void run(){

for(i=1; i<10; i++){
sout("Seeta thread");
try{
Thread.sleep(2000);
} Catch(interpretedexception e) {

         }
      }
   }
}

class yieldDemo{
public static void main(String [] arg){

myThread t = new myThread();
t.start();
t.join(10000);
for(i=1; i<10; i++){
sout("Rama thread");
      }
   }
}
```
> Case:1 Weating of main thread until completing child thread.
if you comment line one then both the main and child excited similutencly and we can't expect exact output.
if you not commenting line one then main thread calls the join method on the child thread object hence main thread will wait until completing child thread in these cases output is "Seeta thread" 10 time and "Rama thread" 10 time.

> Case 2: waiting of the child thread until completing the main thread.
In the above example child thread calls the join method on the main thread object hence child thread has to wait until completing, main thread in this case output is a main thread... followed by the child thread.

> Case 3 if the main thread call join() on the child thread object and the child thread call join() on the main thread object then both the thread will wait forever and the programmer will be stuck (this is something like deadlock)

> Case 4    if a thread calls the join() method on the same thread itself then the program will stuck this is something like a deadlock in this case thread will be waiting an infinite amount of time.


3) sleep(): if the thread doesn't want to perform any operation for a particular amount of time then we should go for the sleep method.
Example: public static native  void sleep() throws InterptedException;
public static native  void sleep(long ms) throws InterptedException; // Not implemented in java
public static native  void sleep(long ms, int ns) throws InterptedException; // implemented in java

> Note: every sleep method throws InterptedException, which checked exception whenever we are using sleep method compulsory we should handle InterptedException either by try-catch or throws key word other wise we will get compile time error.

![sleep_method](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/9b422b3b-c01c-410d-884e-0713fce9fb92)

```
class slideRoter{
public static void main(String []arg)  throws InterptedException {

for(i=1; i<10; i++){
sout("s"+i);
Thread.sleep(5000);
      }
   }
}
```
> How the thread can interrupt to another thread?
a thread can interrupt a sleeping thread or waiting thread by using the interrupt method of thread class ex. public void interrupt(){}.

```
class myThread extends Thread{

public void run(){

for(i=1; i<10; i++){
sout("Seeta thread");
try{
Thread.sleep(2000);
} Catch(interpretedexception e) {
SOUT("we got interrupted demo");
         }
      }
   }
}
```
```
class yieldDemo{
public static void main(String [] arg){

myThread t = new myThread();
t.start();
t.interrupt(10000);  -> line (1)
sout("End of main");
   }
}
```
if we comment line one then the main thread won't interrupt child thread in this case child loop will execute for loop 10 time.
if we are not commenting line one then the main thread interrupts child thread in this case output is  
End of main
Seeta thread
we got interrupted demo

> Note whenever we call the interrupt method if the target thread is not in a sleeping state are waiting for state there is no impact of the interrupt call immediately interrupt call will be wanted until the target thread entered into a sleeping or waiting state
> If a target enters in sleeping or waiting for stat then immediately interrupt the target thread.

If the target thread never entered into a sleeping or waiting state in its lifetime then there is no interrupt call. this is the only case where an interrupted call wested.
| 1 step  | 2 setp |
| ------------- | ------------- |
| ![sleep_method_1](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/22d0ab8e-640b-4adb-bbd2-1857041a7725) | ![sleep_method_2](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/2746903c-e4b7-4ab8-9292-b920959adf9d)  |

> In the above example interrupt call waited until the child thread completes for loop 10000 times.

|Propertiy | yeild()  | join() | sleep() |
|-------------| ------------- | ------------- |-------------|
| 1 purpose | If a thread wants to pass its execution to give a chance for the remaining thread of the same priority then we should go far yield method  | If a thread wants to wait until completing some other threads then we should go for the join method   | If thread don't want to perform any operation for a particular amount of time then we should go for sleep method    |
|2 is a overloaded or not | no  | yes  | yes  |
|3 it is final | no  | yes  | no   |
|4 Is it throws IE? | no  | yes  | yes  |
|5 it is native | yes  | no  | sleep(long ms)--> native and   sleep(long ms, int ns)--> non native |
|6 it is static | yes  | no  | yes |

# Syncrinization
Synchronized is a modifier applicable only for methods and blocks but not for classes and variables if multiple threads are trying to operate simultaneously on the same Java object then there may be a chance of data inconsistency problems 
to overcome this problem we should go for a synchronized keyword if the method or block is declared as synchronized then at a time only one thread allows to execute the method or block on the given object so that the data inconsistency problem will be resolved.
The main advantage of the Syncriniz keyword is we can resolve data inconsistency problems but the main disadvantage of the Syncriniz keyword is it increases the waiting time of the thread and creates performance problems hence if there is no specific requirement then is not recommended to use the Synchronize keyword.

internally Synchronization concept is implemented by using a lock every object in Java has a unique lock whenever you are using the Syncriniz keyword then only the lock concept will come into pitcher.

if your thread wants to execute a Synchronized method on a given object first it has to get the lock of that object one thread got the lock then it is allowed to execute any Synchronized method on that object.
once the method execution complete automatically thread releasing lock 
acquiring releasing lock internally take care by JVM and the programer not responsible for this activity 

while a thread executes a synchronized method on the given object the remaining thread not allowed to execute any synchronized method symultencily on the same object but the remaining thread allows to execute non synchronized methods simultaneously.
```
class x{
sync m1();
sync m2();
m3();

}
// t1 came to excute to m1
// t2 came to excute to m2
// t3 came to excute to m3
```
lock concept implemented based on the object but not based on the method.
![sync_1](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/29dfc6dd-ad98-4125-9f73-8a6259e5deaa )
```
<img src=https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/29dfc6dd-ad98-4125-9f73-8a6259e5deaa" alt="alt text" width="250" height="250">
```
| Synchronized  | Non - Synchronized |
| ------------- | ------------- |
| Whenever we perform the operation {update ADD DELETE REPLACE) ETC. where the state of an object is changing   | Whenever Object state won't be changed like read operation  |

```
class Display{
public synchronized void wish(String name ){
for(int i =0; i<10; i++){
System.out.print("Good Morning");
try{
Thread.sleep(2000);
} catch(InteruptedException e){
System.out.println(name);
}
}
}
}
class MyThread extends Thread{
Display d;
String name;

Mythread(Display d, String name){
this.d = d;
this.name = name;
}

public void run(){
d.wish(name);
}
}
class SynchronizedDemo{
public static void main(String[] args){
Display d = new Display();
MyThread t1 = new MyThread(d,"Dhoni");
MyThread t2 = new MyThread(d,"Yuvi");
t1.start();
t2.start();
}

}
```

>```
>O/P: 
>GoodMornign: Dhoni
>GoodMornign: Yuvi
>
>```
if we are not declaring which method is Synchronized then both threads will be executed simultaneously hence we will get Igreular output.

if we declare which method is Synchronized the at a time only thread will to executed on the given display object hence we will get regular output.
