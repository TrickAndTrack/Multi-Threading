# Multi-Threading
## Intoduction
Two way to define a Thread
1) By extedes Thread class
2) By Imploementaion Runnable
* Geeting and setting Name of Thread
* Thread Priorites
* The method to prevent Thread exceution
   * yeild()
   * join()
   * sleep()
* Synchronization
* Inter Thread Commiunicatio
* DeadLock
* Demon Threads
* Multithreading enchansement

I) multitasking-> divided into two Category
* process based 
* Thread based
* multitasking excluding serveral task simultensly is a concept of multitasking.
   * executing serveral task simuktansly is conept of multitasking.
   * executing serveral task simiultansly where each task a sprate independant program is called process based mutlitasking.
   * executing serveral task simiultansly where each task a sprate independant part of program same program is called Thread based multitasking part & each program independant party called Thead
     
* Whether it is process-based or thread-based, the main objective of multi-threading is to reduce the response time of sections and improve performance.
The main application areas of multithreading are the development of multimedia graphics, animation, and video games. to develop a web-based Windows application server, etc.

Whenever independent jobs are there, there is a best-suited concept of multithreading.

Thread: There is a flow of executions.
We can define threads in two ways: by extending thread classes and by implementing runnable interfaces.

# 1) extending thread class
The main method is executed by the main thread.
The output of threads varies from system to system and JVM to JVM.

## Case 1: Thread shedular
It is a part of JVM that is responsible for scheduler threads, that is if multiple threads are waiting to get a chance of execution. then in which order the thread will be executed is decided by the scheduler.
We cannot expect an exact algorithm followed by a thread scheduler; it varies from JVM to JVM. Hence, we cannot expect thread execution order or execution output.

Hence, whenever the situation comes to multithreading, there is no guarantee for exact output, but we can provide the output as soon as possible.

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


## Case 2 Diffrance Between t.start() & t.run()
#### t.start()
In this case, a new thread will be created, which is responsible for the execution of the run method.
But in the case of t.run(), a new thread won't be created, and the run method will be executed just like a normal method called by the main thread.
Hence, in the above program, if we replace t.start() with t.run(), then the output is a child thread 10 times and allowed by the main thread. 10 times the total output produced by only the main thread.

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


## case 3: importance of thread class start() method.
#### start()
The method is responsible for registering the thread with the thread scheduler and all other mandatory activities. Hence, without executing the thread class start method, there is no chance of starting a new thread in Java. This thread class start method is considered a thread of multithreading.
start():{
1) Register this thread with Thread schedular
2) perform all other madnotery activity
3) Envoke Run() method.
}

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
## Case 4: overloading Run() Method
is always possible thread class start method can invoke no-arg run method other overloaded method we have to call expecitly like a normal method call. 
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


## Case : 6 Overiding of start() method.
if you override start method then over start() Method will be executed just a like normal method call a new thread wont be created.

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

## Case 7:
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

## Case 9: after starting a thread if you are trying to to resatrt the same thread then we will get runtime exception saying IllegalThreadstateException like we are going to get
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
```
myrunnable r = new myrunnable();
thread t1 = new thread();
thread t2 = new thread(r);
```
> [!IMPORTANT]
* Case 1: t.start(); // a new thread will be created which is responsible for the excution of thread class runmethod(), which has emmpty emplimention==
> [!IMPORTANT]
* Case 2: t1.run(); // a new thread wiil not be created and thread class run methid will be excuted just like normal method call.
> [!IMPORTANT]
* Case 3: t2.start(); // a new thread will be created which is responsibe for the excution of my runnable class run method
* Case 4: t2.run(); // a new thread wont be created and my runnable run method will be excuted just like normal method call.
> [!WARNING]  
* Case 5: r.start(); // we will get compile time error. saying my runnable class dosent have start cappiblity  CE: can not find symbole method stop 
> [!WARNING]  
* Case 6: r.run(); // my runnable run method will be excuted like normal method call.

which approch is best to define a thread ->extend or implemting which one is best for thread
among two way define a thread implemtion runnabel approch is recommended in the first approch over class alwasy externs thread class, there is k=no chnace of extednig any other class henac we are messing enhetiance benifit. but in second approch while implmenting runable intrface we can extend any other class, we want any miss inherticae benifit. becous of above resone implmenting runnable interface appoch is recommended that extending thread class.



** thread class constructor **
```
thread t1 = new thread();
thread t2 = new thread(runnable r);
thread t3 = new thread(string name);
thread t4 = new thread(runnable r, string name);
thread t5 = new thread(ThreadGroup g, string g);
thread t6 = new thread(ThreadGroup g, runnable r);
thread t7 = new thread(ThreadGroup g, runnable r, String name);
thread t8 = new thread(ThreadGroup g, runnable r, String name, long stacsize);
```
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

Case study:
```
display d1 = new display();
display d2 = new display();

MyThread t1 = MyThread(d1,Dhoni);
MyThread t2 = MyThread(d2,yuvi);

t1.start();
t2.start();
```
even those whose method is synchronized will get irregular output because threads are operating on different Java objects.
Conclusion: if multiple threads are operating on the same Java object then synchronization is required.
if multiple threads operating on multiple Java objects then synchronization is not required. 

# class-level lock
every class in Java has a unique lock which is nothing but a class-level lock.
if a thread wants to execute a static synchronized method then the thread requires a class-level lock. 
Once the thread got class level lock then it is allowed to execute any static synchronized method of that class.
Once the method execution is complete automatically thread released the lock.

```
class x{
static synchronized m1()
static synchronized m2()
static m3()
synchronized m4()
m5()

}

```
Diagram of execution of the above program. 
![sync_2](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/8f7498d6-ac60-49f9-8298-b33e50ea0ae9)

while thread executing static synchronized method() the reaming threads are not allowed to execute any static synchronized method of that class symultensly remaining threads are allowed to execute the following method execute simultesinly 1) normAL STATIC method 2) synchronized instance method 3)normal instance method.

```
class Display{
public synchronized void displyn(String name ){
for(int i =0; i<10; i++){
System.out.print(i);
try{
Thread.sleep(2000);
} catch(InteruptedException e){
         }
      }
   }
public synchronized void displyc(String name ){
for(int i =65; i<75; i++){
System.out.print((char)i);
try{
Thread.sleep(2000);
} catch(InteruptedException e){
         }
      }
   }
}
class MyThread1 extends Thread{
Display d;

Mythread(Display d){
this.d = d;
}

public void run(){
d.displyn();
}
}

class MyThread1 extends Thread{
Display d;

Mythread2(Display d){
this.d = d;
}

public void run(){
d.displyc();
}
}
class SynchronizedDemo{
public static void main(String[] args){
Display d = new Display();
MyThread t1 = new MyThread(d);
MyThread t2 = new MyThread(d);
t1.start();
t2.start();
}
}
```
> working steps-> 1st excute displayn() mehtod then excute displayc() method.

# Synchronized Block
if very few lines of code are required to synchronize then it is not recommended to declare the entire method Synchronized. we have to inclose those few lines of code by using a Synchronized block.
the main advantage of Synchronized block is it reduces the waiting time of thread and improve performs of the system.

we can declare Synchronized block as follows 
1) to get lock of current objects.
```
   Synchronized(this){
  //area
}
if a thread got lock of current object then only it is allowed to execute this area

```
2) to get a particular object.
```
   Synchronized(b){
  //area
}
if a thread got a locked of a particular object then only it is allowed to execute this area.
```
3) to get the class-level lock

```
   Synchronized(Desplay.class){
  //area
}
if a thread got class level lock of the "Display" class then only it is allowed to execute this area.
```
Example:
```
class Display{
public  void wish(String name ){
;;;;;;;; 1 lakh code line
synchronized(this){
for(int i =0; i<10; i++){
System.out.print("Good Morning");
try{
Thread.sleep(2000);
} catch(InteruptedException e){}
System.out.println(name);
}
}
;;;;;;;; 1 lakh code line
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
Log concept applicable object types and class type but not for primitive hence we cant pass primitive type as argument to synchronized block otherwise we will get compile time error. saying unexpected type found int required reference.

# FAQ 
![FAQ](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/4c215f75-5947-453d-a496-979076653d6a)
2) we can resolve in consistency problem
3) it increases a waiting time of thread and increase a perform opretion.
4) if multiple threads are operating symultensly on the same java object then there may be chance of data inconsistency problems this is called the rest condition. we can overcome this problem by using synchronized keywords. 

Q 8) While a thread executing a synchronized method on a given object is a remaining thread is allowed to execute any other synchronized method simultensly on the same object -> No
Q 9) what is a synchronized Block?
Q 10) how to declare a synchronized Block to get the lock of the current object?
Q 11) how to declare a synchronized Block to get a class level lock?
Q 12) what is the advantage of the synchronized block over the synchronized method?
Q 13) Is a thread that can acquire multiple locks simultensly? yes-> from different objects.
Ans -> ![FAQ_ans_13](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/89f60f5b-b765-4ab5-9a84-bfef49a0be88)

Q 14)  What is a synchronized statement? -> Interview peoeple to create terminology.
the statement present in the synchronized method and synchronized block are called a synchronized statement.

# Inter Thread Communication 

Conclusion 1: Two thread can communicate each other by using wait() notify() and notifyAll() methods
The thread which is expecting updation is responsible to wait() method then immediately thread will enter into a waiting state.
The Thread which is responsible to perform updation after performing updation it is responsible to call notify method then the waiting thread will get the notification and continue its execution with those updated items.

## wait()
## notify()
## notifyAll()

Q) why the above method are in object class?
-> & Conclusion 2:  all methods are present in the object class but not in the thread class because thread can call this method on any Java object.

Conclusion 3:  To call wait() or notify() or notifyAll() method on any object, thread should be owner of that object that is thread should has a lock of that object that is thread should be inside the syncronzed area henace we can call wait and notify and notifyAll method from only synchronized are otherwise we will get a runtime exception saying IllegalmonitarStateException.

Conclusion 4: If a thread calls the wait method on any object it emmidatly releases the lock of that particular object and enters into a waiting state.

If thread calls notify() method on any object it releases the lock of an object that may not immediately except wait() notify() and notifyAll() there is no other method where the thread release lock.

| Method  | Is Thread release lock? |
| ------------- | ------------- |
| yeild()  | No|
| join()  | No |
| sleep()  | No |
| wait()  | Yes |
| notify()  | Yes |
| notifyAll()  | Yes |

Q) which of the following is valid?
1) if threads call wait() method immediately it will enter into a waiting state without releasing any lock
2) if threads call wait() method it releases lock of that object but may not immediately.
3) if threads call wait() method on any object it releases all locks acquired by that thread and immediately enters into the waiting state.
4) if threads call wait() method on any object it immediately releases the lock of that particular object and enters into a waiting state.
5) if threads call notify() method on any object it immediately releases the lock of that particular object.
6) if threads call notify() method on any object it releases lock of that object but my not immediately.
   correct -> 4 and 6.

public final void wait();
public final native void wait(long ms);
public final void wait(long ms, int ns);
public final native void notify();
public final native void notifyAll(long ms);

> Note: Very wait method throws an interpreted exception which is a checked exception hence whenever we are using wait() method compulsory we should handle this interpreted exception either by try-catch or throws keyword other wise we will get compile time error.

```
class ThreadA{
public static void main(String[] arg){
ThreadB b= new ThreadB();
b.start();
synchronized(b){
{
System.out.println("Main Threada calling "); // 1 step
b.wait();
System.out.println("Main Threada got notification ");  // 4th
System.out.println(b.total()); // 5th
}
}
}
class ThreadB extends Thread{
int total =0;
public void run(){
synchronized(this);
{
System.out.println("child Threads calcultion "); // 2nd
b.wait();
for(int i =0; i<=100; i++){
total = total+i;

System.out.println("child Threads given notification" ); // 3rd
this.notify();
}
}
}
```
# Producer consumer problems.
The producer thread is responsible for Producer to the queue and the consumer thread is responsible to consume atoms from the queue, if queue is empty consumer thread method calls the wait method and entered into the waiting state. after Producing atoms to the queue IS RESPONSIBLE to call notify method then the waiting consumer will get that notification and continue its execution with updated atoms.
Example :
![PCP_1](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/4bf89da2-47fe-40bd-9d62-4ce066676088)


### Difference between notify and notifyAll
we can use notify method to give notification to only one waiting thread if multiple threads are waiting then only one thread will be notified the remaining thread have to wait for further notification. 
Which thread will be notified we can't expect it depends on JVM.

We can use notifyAll to give notifications for all waiting threads of your particular object even though multiple threads are notified but execution will be performed one by one because threads are required to lock and only one lock is available.
> Note: on which object we are calling the wait method thread required the lock of that particular object if we are calling the wait method on S1 then we have to get the lock of the s1 object but not the s2 object.

Stack s1 = new Stack();
Stack s2 = new Stack();
```
synchronization (s1){
s2.wait()
}
RE: IllegalMoniterzaException
```
------------------------------------
```
synchronization (s1){
s1.wait()
}
> correct one
```
# Dead lock
If two thread are waiting for each forever sach type of infinite waiting is called Deadlock.
synchronization keyword is only resone for deadlock situvation henace while using synchroniz keyword we have to take spaecial care there is no resolvtion for deadlock but servral prevtntion tachnique are avialable.

# deadLock vs starveation
long waiting of a thread where waiting neverends is called deadlock.
where as long waiting of a thread where waiting ends at certan point is called startvation.
Low priority thread has to wait untill completing all high priority threads it may be long waiting but ends a yet certun point is called which is nothing but starvation.

# Daemon Thread
The Thread which is excuting in background
Example 1) Attach Lister, Signal Dispatcher, Gc
The Threads which are excuting in background are called "Daeomn Threads".
The main objective daemon thread is to provide support for non daemon threads the main threaad.
for example if main thread run with low memory then GVM run GC() to distory the useless Object so that number of bite of free meoery will be improved with this free memory main thread can continiew its excution.

Usually, Daemon thread have low priority but based on our requirement daemon threads can run with high priority also.
we can check the daemon nature of a thread by using is daemon method of thread class.
1) public boolean isDaemon();

we can change the daemon nature of thread by using setDaemon nature.
1) public void setDaemon(boolean b)
but changing daemon nature is possible before starting of thread only after starting a thread if we are trying to change daemon naeture then we will get a runtime exception saying illegalthreadexception.

# Deafult nature 
by default main thread is always non-daemon & all reaming threads are daemon threads nature will be inherited parent or child if the parent thread is a demon then ai=utoomaticly child thread is also daemon and if the parent thread is non-daemon then automatically child thread is also non-daemon.
it is impossible to change the daemon nature of the main thread it is already started by JVm by binging.
whenever the last non-daemon thread terminates automatically all daemon thread will be terminated irrespective of there positon.
# FAQ 
What is green Thread?

. ) Java multithreading condcept is implemet=nting by using the following two models 
1) green thread model
2) native voice model

### Green thread model
a thread which is managed completely by JVM without taking underlying OS support is called Green Thread.
very few operating systems like Sun Sources provide support for the green thread model.
green thread model is deprecated and not recommended to use.

# native OS model
The thread which is managed by JVM  with the help of the underlying OS, is called the native OS model.
All Windows-based operating systems provide support for native OS models.

How to stop a thread? t.stop();
we can stop() a thread execution by using the stop method of threading a class
public void stop method
if the call-stop method is immediate thread will enter into a dead state.
anyway stop method is deprecated and not recommended to use.

### how to suspend and resume a thread.
t.suspend();
how can we resume suspend thread?
t.resume();

we can suspend a thread by using suspend() method of the thread class. then immediately thread will be entered into a suspended state.
we can resume a suspended thread by using the resume() method of the thread class then the suspended thread can continue its execution.
public void suspend();
public void resume();
> Anyway these methods are deprecated and not recommended to use.

# life cycle Image
![Life_Cycle](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/e269205d-88fc-4b8c-b16e-48f37bd234fb)

* Enhancement Multithreading* 
# ThreadGroup
based on functionality we can group threads into a single unit which is nothing but a thread group is thread group contains a group of threads in addition to threads thread group can also contain sub-threads groups.
The main advantage of maintaining threads in a thread group is we can perform common operations easily.

every thread in Java belongs to some group main threads belong to main group.
every thread group in java is a child group of the system group either directly or indirectly hence system group accesses root for all thread groups in Java.

SYstem-group contains several system-level threads like finalized, reference handler,
singal dispatcher, attache listner.
![image](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/54bb327a-dbb7-4a27-9ede-14677d8bca10)

Thread group is a Java class present in Java.lang package it is a direct child class of object.
### Constructor 
1) ThreadGrouo g = new ThreadGrouo(String name);
Create a new thread group with a specific group name.
the parent of the new group is the thread group of the currently existing thread.

3) ThreadGrouo g = new ThreadGrouo(ThreadGroup m, String GroupName);
Create a new thread group with a specific group name.
the parent of the new group is the specified parent group.
ThreadGrouo g1 = new ThreadGrouo( g1, "Group Name");

```
class Test{
public static void main(String[] args){
ThreadGrouo g = new ThreadGrouo("First group Name");
System.out.println(g1.getParent().getName()); // main
ThreadGrouo g2 = new ThreadGrouo(g1, "Second group name");
System.out.println(g2.getParent().getName()); // First group Name
}
}
```
# important methods of Thread group class.
1) String getName() ; // return name of group
2) int getMaxPriority(); //  return max priority of thread group
3) void setMaxPriority(int p); //  to set maximum priority of thread group & difualt max priority is 10.
Threads in the threads group that already have higher priority wont be effected but for newly added threads with this max priority is applicable.

```
class Test{
public static void main(String[] args){
ThreadGrouo g1 = new ThreadGrouo("to");
Thread t1 = new Thread(g1, "Thread1");
Thread t2 = new Thread(g1, "Thread2");
g1.setMaxPriority(3)
Thread t3 = new Thread(g1, "Thread3");
System.out.println(t1.getPriority()); //5
System.out.println(t2.getPriority());// 5
System.out.println(t3.getPriority()); // 3
}
}
```
![image](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/e65f055c-9c3b-48bd-ab07-eee1e698e8fb)

4)ThreadGroup getParent(); // return parent group of current thread.

5) void list(); // its aprint informtion about thread  group to the console.

6) int activeCount(); // returns number of active threads present in thread group.

7) int activeGroupCount(); // returns the number od active group prsent in current thread group.

8) int enumerate(Thread[] t); // to copy all active threads of this thread group into a provided thread [].
int this subgroupThread also will be considered.

9) int enumerate(ThreadGroup[] t); // to caopy all active subThreadgroup into thread group[].

10) boolean isDaemon(); // to check whether the thread group is daemon or not.

11) void setDaemon(boolean b); //  

12) void interrupt(); // to interrupt all waiting or sleeping thread preset in a thread group.

13) void destroy(); // to destroy thread group and sub-thread groups.

write a program to display all active threads' name belongs to system grops and child groups.
```
class ThreadGroupDemo4{
public static void main(String[] args){

ThreadGroup system = Thread.currentThread().getThreadGroup().getParent();
Thread[] t = new Thread[sysytem.activeCount()];
system.enumerate(t);
for(Thread t1 : t){

System.out.println(t1.getName()+ "----" + t1.isDaemon());
}}}
```
# java.util.concurrent
The problem with the traditional synchronize keywords
1) we are not having any flexibility to try for a lock without waiting.
2) There is know way to specific max waiting time for a thread to get locked so that thread will wait until getting locked which may create a performance problem that may cause deadlock.
3) if threads released a lock which waiting thread will get that lock we are not having any control over this.
4) there is no API to list all waiting threads for a lock.
5) synchronize keyword compulsory we have to use either at the method level or within a method and it is not possible to use across multiple method().
> To overcome this problem sum people introduce java.util.concurrent.lock package in 1.5 v.
> its also provide several enhance ment to programmer to provide more control to concurrency.


# lock intraface
lock object similar to an implicit lock acquired by a thread to execute a synchronized method or synchronized block.
lock implementation provides more extensive operation than the traditional implicit lock.

# Important methods of lock intraface
1) void lock(); // we can use this method to acquire a lock. if the lock already available then the current thread will get that lock. if the lock is not already available then it will wait until getting locked. it is exactly same behavior of the traditional synchronized keyword.

2) boolean tryLock(); // to acquired lock without waiting, if the lock is available then thred acquired the lock and return true. if the lock is not available then this method flase and continue execution without waitiing this case thread never be entered into the waiting state.

3) boolean tryLock(long time, Timeunit unit); // if lock is available then the thread will get the lock and continue its execution. if the lock is not available then thread will wait until a specified amount of time still, lock is not available then can continue its execution.

4) void UnLock(); // To release a lock 

# TimeUnit
TimeUnit is an enum prsent in java.util.cocurrent package.
```
if(l.tryLock(1000, TimeUnit Miliseconde)){
}
```

# ReententrLock();
it is the implementation of the lock interface and it is a direct child class of the Object.

Reenterent means a thread can acquire same lock multiple time wihtout any issues, internally reenter lock increments the thread personal count whenever we call the lock method and the decrement count value whenever threads call unlock method lock will be released whenever count reaches zero.

ReententrLock l = new ReententrLock();
creates an instance of ReententrLock
ReententrLock l = new ReententrLock(boolean fairness);
creates a ReententrLock with given fairness policy.
if fairness is true then the longest waiting thread can acquire cac lock if it is available it follows a first come first serve policy.
if fairness is false then which waiting thread will get a chance we cant expect?
the difficult value for fairness is false.
Q) 1 Which of the following declaration are equal?
ReententrLock l = new ReententrLock();
ReententrLock l = new ReententrLock(true);
ReententrLock l = new ReententrLock(false);
All the Above
Ans-> 1 and 3.

An important method of Reentern lock.
1) void lock()
2) boolean tryLock()
3) boolean tryLock(long l, TimeUnit t)
4) void lockInterruptibly()
5) void unlock()

Extra Methods
1) int getHoldCount() // return number of hold on this lock by the current thread.
2) boolean isHeldByCirrentThread() // boolean is held by current thread. returns true if and only if lock hold by current thread
3) int getQueueLength() // in get Queue length returns the number of thread waiting for the lock
4) Collection getQueuedThreads() // collection get Qued threads it return a collection of thread which are waiting to get locked
5) boolean hasQueuedThreads() // returns true if any threads  to get locked
6) boolean isLocked() //  returns true if locked aqured by some thread
7) boolean isFair() // returns true retuns true if the fair ness policy is set with true value.
8) Thread getOwner() // returns the thread which aqured lock.
![image](https://github.com/TrickAndTrack/Multi-Threading/assets/73180409/da28771a-5704-48f6-8cad-06f30a17d874)

 ```
Import java.util.concurrent.locks.*;

class Display{
ReententrLock l = new ReententrLock();
public  void wish(String name ){
l.lock(); // ---- line 1
for(int i =0; i<10; i++){
System.out.print("Good Morning");
try{
Thread.sleep(2000);
} catch(InteruptedException e){
}
System.out.println(name);
}
l.unlock(); // ---- line 2
}
}
class MyThread extends Thread{
Display d;
String name;
My thread(Display d, String name){
this.d = d;
this.name = name;
}
public void run(){
d.wish(name);
}
}
class ReentrantLockDemoDemo{
public static void main(String[] args){
Display d = new Display();
MyThread t1 = new MyThread(d,"Dhoni");
MyThread t2 = new MyThread(d,"Yuvi");
MyThread t3 = new MyThread(d,"Ganguly");
t1.start();
t2.start();
t3.start();
}

}
```
if we comment on lines one and two then the thread will be executed simultensly and we will get output if we are not commenting on lines one and two then the threads will be executed one by one and we will get regular output.

# Demo Program for tryLock() ~
```
Import java.util.concurrent.locks.*;
class MyThread extends Thread{
ReententrLock l = new ReententrLock();
MyThread(String name){
super(name);
}
public void run(){
if(l.tryLock()){
System.out.println(Thread.currentThread()+getName()+"...got lock and performing safe operations");
try{
Thread.sleep(2000);
}catch(InteruptedException e)
{}
l.unlock();
}
else{
System.out.println(Thread.currentThread().getName()+".. unable to get lock and hence performing alternative operations" );
}
}
}
class ReentrantLockDemoDemo{
public static void main(String[] args){

MyThread t1 = new MyThread("First Thread");
MyThread t2 = new MyThread("Second Thread");
t1.start();
t2.start();
}

}
```
```
Import java.util.concurrent.locks.*;
Import java.util.concurrent.*;

class MyThread extends Thread{
ReententrLock l = new ReententrLock();
MyThread(String name){
super(name);
}
public void run(){
if(l.tryLock(5000, TimeUnit.MILLISECONDS)){
System.out.println(Thread.currentThread()+getName()+"...got lock");
try{
Thread.sleep(3000);
l.unlock();
}catch(InteruptedException e)
{}
l.unlock();
System.out.println(Thread.currentThread().getName()+".. Releases lock" );
break;
}
else{
System.out.println(Thread.currentThread().getName()+".. unable to get lock and wiill try again" );
}
}catach
(Exception e){}

}
while(true);
}
}
class ReentrantLockDemoDemo{
public static void main(String[] args){

MyThread t1 = new MyThread("First Thread");
MyThread t2 = new MyThread("Second Thread");
t1.start();
t2.start();
}
}
```
# Threads pools
Threads pool Creating a new thread for every job may create performace and memory problems to overcome this we should go for a thread pool.
The thread pool is a pool of already created thread ready to do our job Java 1.5 version introduces framework to implement thread pool 
Thread pool framework also known as executor framework.
we can create thread pool as follows
Ex: ExcutorService service =  Excutors.newFixedThreadPool(3);
we can submit a runnable Job by using submit method().
service.submit(job);
we can shutdown executors service by using.
service.shutdown();

```
Import java.util.concurrent.*;
class PrintJob implements Runnable{
String name;

PrintJob(String name){
this.name = name;
}
public void run(){

System.out.println(name + " Job started by thread "+ Thread.currentThread()+getName());
try{
Thread.sleep(5000);
}catch(InteruptedException e)
{}
System.out.println(name + " Job completed by thread "+Thread.currentThread().getName());

}
}
class ExcutorDemo{
public static void main(String[] args){
PrintJob[] jobs = { new PrintJob("A"),  new PrintJob("B"),  new PrintJob("C"),  new PrintJob("D"),  new PrintJob("E")};

ExecutorService service = ExecutorService.newFixedThreadPool(3);
for(PrintJob job: jobs)
{
service.submit(job);
}
service.shutdown();
}
}
```
in the above example 3 thread responsible to execute 6 jobs so that a single thread can be reused for multiple jobs.
> Note: while designing web server & application servers we can use thread pool concept.

> What is a diffrance beween Collable and Runnable?

# Callable and Future:
in the case of runnable thread wont return anything after completing a job, if a thread is reured to return result after excution then we should go for callable.

Callable interface have only one method call.
```
public Object call() throws exception;
```
if we submit callable object to excutor then after compelting the job threads return and object of type future. that is furutre object can be used to retrive result from callable job.
```
Import java.util.concurrent.*;
class MyCallable  implements Callable{

int num;
MyCallable(int num){
this.num = num;
}
public Object call() throws Exception{

System.out.println( Thread.currentThread()+getName() + "is.. resposible to find sum of first "+ num +"number");
 int sum=0;

for(int i=1; i<=num; i++){
sum = sum+i;
}
}
return sum;
}
}

class CallableFutureDemo{
public static void main(String[] args) throws Exception{
MyCallable[] jobs = { new MyCallable(10),  new MyCallable(20),  new MyCallable(30),  new MyCallable(40),  new MyCallable(50)};

ExecutorService service = ExecutorService.newFixedThreadPool(3);
for(MyCallable job: jobs)
{
Future f = service.submit(job);
System.out.println(f.get());
}
service.shutdown();
}
}
```

|Runnable | Callable |
|-------------| ------------- |
|If a thread is not required to return anything after completing JOb then we should go for runnable | If a thread is required to return something after completing Job then we should go for callable  |
| Runabble interface contains only one method Run() | Callable contains only one method call()  |
| Runnable Job not required to return anything and hence the return type of run method is Void| Callable Job is required to return something and hence the return type of call method is Object  |
|With a run method if there is any chance of a rising checked exception compulsory we should handle it by using try catch because we can't use the throws keyword runmehtod| inside call method if there is any chance of rising checked exception we are not required to handle by using try catch because call method already throws exception  |
| Runnable interface present in Java.lang package | Callable interface present in java.util.concurrent package |
|introduce in 1.0 V| introduce in 1.5 v|

# ThreadLocal
ThreadLocal class provides thread-local variables thread-local class maintains value per tread bases each thread-local object maintains a separate value like userID transaction ID extra for each thread that exceeds that object.
Thread can access its local value, can manipulate its value, and even can remove its value and in every part of the code which is executed by the thread we can access its local variable.

Ex consider a servlet Which invokes the sum business method we have required to generate a unique transaction Id for reach ad every request & we have to pass this transaction id to the business method for this requirement we can use this ThreadLocal to maintain separate trnsactrionID for every request that is for every thread.

> Note 1) ThreadLocal class introduced in 1.2 V & enhanced in 1.5 V
> thread local can be associated with thread scope.
> Total coat which is executed by thread has access to corresponding Thread localveribale.
> Thread can exccess its own localveribale and cant access other threads localveribale.
> Ones the thread is entered into deat state all its local variable are bydifult available for garbage collection.

> Q) How to create ThreadLocal variable?

Constructor => Threadlocal tl = new ThreadLocal(); Create a ThreadLocal variable.
Methods => Object.get(); // return the value of thread localveribale associated with the current thread.
Object initialValue(); // returns the initial value of the thread local variable associated with the current thread. the default implementation this method returns null. to customize over own initial value we have to override this method.
void set(Object newvalue); //  to set a new value 
void remove(); // to remove the value of thread-local variable to assisted with current thread.
it is newly added method in 1.5V.
after removal, if we are trying to access it will be reinitialized once again by invoking its initial value method.
```

Class ThreadLocalDemo1{

public static void main(String[] args){
ThreadLocal tl = new ThreadLocal();

{
public Object initalValue(){
 return "XYZ"
}

}

Stystem.out.println(tl.get()); // null 
tl.set("XYZ");
Stystem.out.println(tl.get()); // XYZ
tl.remove();
Stystem.out.println(tl.get()); // null
}
}
```
overriding of the initial value of the method.


```
class CustomerThread extends Thread{
static Integer custId= 0;
private static  ThreadLocal tl = new ThreadLocal();
{
protected Integr initialValue(){

return ++cystId;
}

};

CustomerThread(String name){
super(name);

}
public void run(){
System.out.println( Thread.currentThread()+getName() + "excuting with customer id:" + tl.get());
}
}

Class ThreadLocalDemo2{

public static void main(String[] args){
ThreadLocal tl = new ThreadLocal();{
CustomerThread c1 = new CustomerThread("Thread-1");
CustomerThread c2 = new CustomerThread("Thread-2");
CustomerThread c3 = new CustomerThread("Thread-3");
CustomerThread c4 = new CustomerThread("Thread-4");
c1.start();
c2.start();
c3.start();
c4.start();
}
}
```
The above program for every customer thread a separate customer Id will be maintained by the thread-local object.
ThreadLocal Vs inherti
