В проекті має бути реалізовано функціонал виведення нумерованого переліку
фруктів за допомогою можливостей багатопотоковості. Виведення має бути таким:


Thread 1: (1) orange (2) apple (3) plum (4) mango
Thread 2: (1) orange (2) apple (3) plum (4) mango

1) Створіть проект Multithreading-Fruits на локальній машині через IntelliJ IDEA (IDE).

(2) Структура проекту має бути такою:

(3) Функціонал класу Main

package app;

public class Main {

    public static void main(String[] args) {
        DataHandler dataHandler = new DataHandler();
        MyThread myThread1 = new MyThread("Thread 1", dataHandler);
        MyThread myThread2 = new MyThread("Thread 2", dataHandler);
        myThread1.start();
        myThread2.start();
    }
}


(4) Функціонал класу DataRepository

package app;

public class DataRepository {

    public String[] getData() {
        return new String[] {"orange", "apple", "plum", "mango"};
    }
}

(5) Доопрацюйте функціонал класу DataHandler

package app;

import java.util.concurrent.atomic.AtomicInteger;

public class DataHandler {

    String[] fruits = new DataRepository().getData();

    public void getOutput() {
        // критичний блок коду
        synch (this) {
            StringBuilder sb = new StringBuilder();
           count = new AtomicInteger(1);
            for (String fruit : fruits) {
                sb.append(String.format("(%d) %s ",
                        count, fruit));
            }
            System.out.println(currentThread().getName() + ": " + sb);
        }
    }
}

(6) Доопрацюйте функціонал класу MyThread

package app;

class MyThread extends  {

     dataHandler;

    public MyThread(String name, DataHandler dataHandler) {
        super(name);
        this.dataHandler = dataHandler;
    }

    public  run() {
        dataHandler.getOutput();
    }
}

(7) Залийте виконаний проект на свій GitHub репозиторій, посилання на який зазначте в LMS.
