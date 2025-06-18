
1) Унаследоваться от класса Thread
2) Реализовать интерфейс Runnable

# Останговка потока 

1) `thread.stop()` - устаревший нерекомендованный, тк при вызове этого метода происходит немедленная остановка потока, что может привести к потере/повреждению данных при работе с БД, например
2) `thread.interrupt()` - устанавлеват `true` в поле `Thread.currentThread.isInterrupted`, после этого нужно явно просписать в `run()`, что при `isInterrupted = true` нужно остановиться
3) `thread.setDaemon(true)`

# Методы синхронизации 

1) Могут быть синхронизированные методы, для этого используем сигнатуту: `public synchronized void name() {}`
2) Добавляем поле `private Object monitor = new Object()` и в методе пишем ключевое слово и передаем монитор `synchronized(monitor) {}`

# Атомарные типы данных 

`private AtomicInteger value = new AtomicInteger()`

`value.getAndIncrement()`

`value.getAndDencrement()`

в таком случае синхронизация, тк атомарные тд выполняют операции за одну итерацию 

# Volotile

Ключевое слово `volotile` запрещает кешировать переменную (сохранять значение в локал память)

# CountDownLatch

<img width="565" alt="image" src="https://github.com/user-attachments/assets/71f07b3f-e935-44aa-a086-ae4ed2eb7bdb" />

# ExecutorSerice

<img width="741" alt="image" src="https://github.com/user-attachments/assets/bbcb7008-b131-447e-bad5-d196ca32090a" />

`executorSerice.shutdown()` - остановка сервиса

# Потокобезопасные коллекции 

<img width="1111" alt="image" src="https://github.com/user-attachments/assets/24ff6e8c-c95e-4b16-b4ae-d760c3a8a161" />

