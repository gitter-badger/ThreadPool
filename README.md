ThreadPool
==========

A Linux environment ThreadPool

UserGuide
==========
The default thread number is 10, if you want to increase number call setMaxThread().
There is two method to start the threads, one is start() it will start only one thread to process the jobs, the other is startAll() it will start the all the thread to process the jobs. How to use it, it's up to you.

Compile
==========
Very easy to compile it, just make.

Example
==========

void *run(void *arg);

int main(){

  ThreadPool *tp=new ThreadPool();
  int *num=(int*)malloc(sizeof(int)*19);

  for(int i=0;i<19;i++){
    num[i]=i;
    tp->addJob(run,&num[i]);
  }
  tp->startAll();
  sleep(5);
  delete tp;
  
  return 0;
}


void *run(void *arg){
  int *num=(int*)arg;
  printf("Thread is %x,  Num %d \n",pthread_self(),*num);
}