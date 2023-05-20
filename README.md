# TMP
# Практика 0
```
@startuml
left to right direction
skinparam packageStyle rect

actor эксперт
actor соискатель_грантов
actor держатель_фонда

rectangle информационная_система_технической_экспертизы {
  
  соискатель_грантов--(подача заявки)
  соискатель_грантов--(выгодная презентация)

  (подача заявки) .> (независимая экспертиза)

  эксперт--(рассмотрение заявок)
  эксперт--(независимая экспертиза)
  
  (независимая экспертиза).> (выдача гранта)

  держатель_фонда--(оценка результата экспертизы)
  держатель_фонда--(выдача гранта)

}
@enduml
```
![0](https://user-images.githubusercontent.com/132086384/235200383-64ed4412-838e-4122-9927-d8e4186b286a.png)

# Практика 1
```
@startuml
left to right direction
title Система технической экспертизы
actor Эксперт
actor Соискатель_грантов
actor держатель_фонда
rectangle Система {
держатель_фонда -- (организация мероприятия)
(организация мероприятия) ..>(подача заявки):<<include>>
(организация мероприятия) ..> (независимая экспертиза):<<include>>
(организация мероприятия) ..> (оценка результатов экспертизы):<<include>>

Соискатель_грантов -- (подача заявки)
(подача заявки) ..> (Выдача гранта):<<include>>
(независимая экспертиза) ..> (Выдача гранта):<<include>>
(оценка результатов экспертизы) ..> (Выдача гранта):<<include>>
Эксперт -- (независимая экспертиза)
}
@enduml
```
![2](https://user-images.githubusercontent.com/132086384/235200464-fb5ce4a3-cc00-4a70-810f-a2d3091be6d1.png)
```
@startuml
class Эксперт{
+Паспортные данные
+ФИО
+Должность
Проверка()

}

class Соискатель_грантов{
+Паспортные данные
+ФИО соискателя
+Номер гранта
Регистрация Гранта()
}

class Грант{
+Номер гранта
+ФИО Представителя гранта
+Презентация Гранта
}

class Держатель_фонда{
+ФИО
+Должность
Оценка результата экспертизы()
Выдача гранта()
}

class СтатусГранта{
+Номер гранта
+Статус Гранта
+Отчет об экспертизе
}

class Выполнено{
+Грант проверен
}

Эксперт --> Грант:Проверяет
Соискатель_грантов --> Грант:Регистрация гранта
Держатель_фонда --> Грант:Выдает
Эксперт --> СтатусГранта:Изменяет статус
Держатель_фонда --> СтатусГранта:Оценивает результат экспертизы
СтатусГранта --> Выполнено
Грант --> Выполнено
Выполнено --> ВыдачаГранта
@enduml
```
![1](https://user-images.githubusercontent.com/132086384/235200520-78983f69-d306-4507-8fa9-f4284f3899a7.png)

# Практика 2
```
@startuml
title Информационная система технической экспертизы: диаграмма последовательности
skinparam backgroundcolor AntiqueWhite/Gold
participant Соискатель
participant Заявка
participant Эксперт 
participant Держатель_фонда
participant Грант
activate Соискатель
Соискатель -> Заявка: подает заявку
activate Заявка
Заявка -> Эксперт : Выдает заявку
deactivate Соискатель
activate Эксперт 
Эксперт -> Заявка:Оценивает заявку
Заявка-> Держатель_фонда:Заявка одобрена
deactivate Заявка
activate Держатель_фонда
Держатель_фонда -> Грант:Принимает решение о выдаче грантов
deactivate Держатель_фонда
activate Грант
Грант-> Соискатель:Выдает грант
deactivate Эксперт 
activate Соискатель
@enduml 
```
![3](https://user-images.githubusercontent.com/132086384/235200645-ca73e83e-ceaf-4771-86b3-813a8a0cb096.png)
```
@startuml
left to right direction
title Система технической экспертизы: диаграмма развертывания
skinparam backgroundcolor AntiqueWhite/Gold
database Заявка
node ПК_Эксперт
node ПК_Соискатель
node ПК_Держатель_фонда
node Грант
node Система_экспертизы

ПК_Эксперт - Заявка: Проверяют
ПК_Соискатель - Заявка: Подают
ПК_Эксперт - Система_экспертизы: Используют
ПК_Держатель_фонда - Заявка: Оценивает
ПК_Держатель_фонда - Грант: принимает решение
Грант - ПК_Соискатель: Выдает грант
@enduml
```
![4](https://user-images.githubusercontent.com/132086384/235200917-d7457f6d-9d47-4e0a-9493-de6af736525b.png)

# Практика 3
# Стратегия
```
@startuml
title Пратическая работа 3: Strategy
class Variant{
selection()
}
class Game{
strategy: Variant
init()
play()
}

class Paper{
selection()
}
class Rock{
selection()
}
class Scissors{
selection()
}
class Pencil{
selection()
}
class Fire{
selection()
}
class main{
int n
str vibor
playtime()
player1.play(player2)
}
note right of main::"playtime()"
player1 = playtime(vibor)
player2 = playtime(vibor)
end note

Paper --> Variant
Rock --> Variant
Scissors --> Variant
Pencil --> Variant
Fire --> Variant
main *--> Variant
main --Game
@enduml
```
<img width="672" alt="5" src="https://github.com/dabrokeb/TMP/assets/132086384/91af6822-4e3b-4059-aee4-26e29045d937">

# Шаблонный метод
```
@startuml
title Пратическая работа 3: Template Method
class Algorithm{
template_method()
flagstock()
draw_1()
draw_2()
draw_3()
final()
printer()
}
note right of Algorithm::"template_method()"
self.flagstock()
self.draw_1()
self.draw_2()
self.draw_3()
self.final()
self.printer()
end note

class colors{
painwhite()
painred()
painblue()
}

class RussianFlag{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
final()
}
class  Austria{
z = colors
z.pain
draw_1()
draw_2()
draw_3()
}

Algorithm <|-- Austria :Немецкий флаг
Algorithm <|-- RussianFlag : Российский флаг

RussianFlag -  Austria
(RussianFlag, Austria) - colors:Задает цвет
@enduml
```
![6](https://github.com/dabrokeb/TMP/assets/132086384/63f13357-4119-44dd-a9ed-08716a937298)

# Итератор

```
def alphabets_upto(letter):
    for i in range(65, ord(letter)+1):
            yield chr(i)
 
if __name__ == "__main__":
 
    alphabets_upto_K = alphabets_upto('K')
    alphabets_upto_M = alphabets_upto('M')
 
    for alpha in alphabets_upto_K:
        print(alpha, end=" ")
 
    print()
 
    for alpha in alphabets_upto_M:
        print(alpha, end=" ")

def inBuilt_Iterator1():
     
    alphabets = [chr(i) for i in range(65, 91)]
     
    for alpha in alphabets:
        print(alpha, end = " ")
    print()
 
def inBuilt_Iterator2():
     
    alphabets = [chr(i) for i in range(97, 123)]
     
    for alpha in alphabets:
        print(alpha, end = " ")
    print()
 
if __name__ == "__main__" :
    inBuilt_Iterator1()
    inBuilt_Iterator2()
```

Результат программы:

```
A B C D E F G H I J K 
A B C D E F G H I J K L M A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 
a b c d e f g h i j k l m n o p q r s t u v w x y z
```
# Практика 4
## Диаграмма

```
@startuml
interface Iterator.Iterator {
+ boolean hasNext()
+ Object next()
}
interface Iterator.Aggregate {
+ Create Iterator()
+ Iterator()
}
class Iterator.Concrete_Iterator {
+ {static} void hasNext():Next
}
class Iterator.Concrete_Aggregate {
+ {static} void Create Iterator():Iterator
}

Iterator.Iterator <|..|> Iterator.Aggregate
Iterator.Aggregate ..> Iterator.Concrete_Iterator
Iterator.Concrete_Iterator ..> Iterator.Iterator
Iterator.Concrete_Aggregate ..> Iterator.Aggregate
@enduml
```

![iterator](https://github.com/dabrokeb/TMP/assets/132086384/7b82b3ec-0f6e-49ad-a10b-d9256d60b1fd)


# Посетитель

```
class Studying_In_Institute:
 
    def accept(self, visitor):
        visitor.visit(self)
 
    def teaching(self, visitor):
        print(self, "Taught by ", visitor)
 
    def studying(self, visitor):
        print(self, "studied by ", visitor)
 
    def __str__(self):
        return self.__class__.__name__
 
class SDE(Studying_In_Institute): pass
 
class STL(Studying_In_Institute): pass
 
class DSA(Studying_In_Institute): pass
 
class Visitor:
 
    def __str__(self):
        return self.__class__.__name__
 
class Instructor(Visitor):
    def visit(self, crop):
        crop.teaching(self)
 
 
class Student(Visitor):
    def visit(self, crop):
        crop.studying(self)
 
sde = SDE()
stl = STL()
dsa = DSA()
 
instructor = Instructor()
student = Student()
 
sde.accept(instructor)
sde.accept(student)
 
stl.accept(instructor)
stl.accept(student)
 
dsa.accept(instructor)
dsa.accept(student)
```

Вывод программы:

```
SDE Taught by  Instructor
SDE studied by  Student  
STL Taught by  Instructor
STL studied by  Student  
DSA Taught by  Instructor
DSA studied by  Student 
```

## Диаграмма

```
@startuml
interface Visitor.Studying_In_Institute {
+ void accept()
+ void teaching()
+ void studying()
}
class Visitor.Instructor {
+ void visit()
+ void teaching()

}
class Visitor.Student {
+ void visit()
+ void studying()
}
class Visitor.SDE {
+ void create(ProjectClass)
+ void create(DataBase)
+ void create(Test)
}
class Visitor.STL {
+ void beWritten(Developer)
}
class Visitor.DSA {
+ {static} void main(String[])
}

Visitor.DSA <|.. Visitor.Student
Visitor.DSA <|.. Visitor.Instructor
Visitor.SDE <|.. Visitor.Student
Visitor.SDE <|.. Visitor.Instructor
Visitor.STL <|.. Visitor.Student
Visitor.STL <|.. Visitor.Instructor
Visitor.Studying_In_Institute <|.. Visitor.Instructor
Visitor.Studying_In_Institute <|.. Visitor.Student
@enduml
```
![visitor](https://github.com/dabrokeb/TMP/assets/132086384/07f237b8-25f6-4e74-a8b2-e67594869a3b)


