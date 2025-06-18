# Способы создания 

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
   
