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

