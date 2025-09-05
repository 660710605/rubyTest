## 📕 การต่อสตริงใน ruby

คือ การนำสตริงตั้งแต่ 2 สตริงขึ้นไปมาต่อกัน โดยใน Ruby ทำได้หลายวิธีดังนี้


## 1.ใช้เครื่องหมาย +
  - การใช้เครื่องหมาย + ต่อสตริง ใช้ได้แค่ String + String เท่านั้น
  - ถ้าเป็น String + int จะเกิด error ต้องทำการแปลง int เป็น String ก่อน โดยใช้เมธอด to_s


```ruby
myString = "Welcome " + "to " + "Ruby!"
puts myString
```

<details close>
 <summary><b>output</b></summary>
 <pre>
 Welcome to Ruby!
 </pre>
</details>


เพื่อให้กระชับ สามารถละเว้นเครื่องหมาย + ได้
```ruby
myString = "Welcome " "to " "Ruby!"
puts myString
```

<details close>
 <summary><b>output</b></summary>
 <pre>
 Welcome to Ruby!
 </pre>
</details>


## 2.ใช้เครื่องหมาย <<
  - การใช้เครื่องหมาย << ต่อสตริง สามารถใช้ String + String หรือ String + int ก็ได้
  - เป็นการต่อสตริงที่เปลี่ยนสตริงต้นฉบับ -> → เมื่อมีการเก็บ String ไว้ในตัวแปรหนึ่ง แล้วทำการต่อสตริงกับตัวแปรนั้น
    ถ้าลองพิมพ์ค่าตัวแปรที่เก็บ String ที่ถูกต่อ จะเห็นว่า String เปลี่ยนไป นั่นคือ สตริงต้นฉบับเปลี่ยนไปด้วย


### กรณี String + String

```ruby
myString = "Welcome " << "to " << "Ruby!"
puts myString
```

<details close>
 <summary><b>output</b></summary>
 <pre>
 Welcome to Ruby!
 </pre>
</details>

### กรณี String + int
  Ruby จะแปลง ตัวเลข เป็นรหัส UNICODE (65 คือ A ใน UNICODE )

```ruby
message = “This ” << “is ” << 65
puts message
```

<details close>
 <summary><b>output</b></summary>
 <pre>
 This is A
 </pre>
</details>

## 3.ใช้เมธอด concat
  - เราสามารถส่ง argument ที่อยู่ในวงเล็บ เป็น String หรือ หรือ int ก็ได้
  - โดย เป็นการเปลี่ยน String ที่ object นั้นเลย ก็คือเปลี่ยนที่ String ต้นฉบับ
    หมายความว่า ถ้ามีตัวแปรที่เก็บ “foo” อยู่
    แล้วลองพิมพ์ค่าตัวแปรนั้นออกมาดู หลังจากที่ได้ต่อสตริงโดยใช้เมธอด concat แล้ว
    ตัวแปรนั้นจะเปลี่ยนเป็นสตริงใหม่ที่ได้ทำการต่อสตริงแล้ว

### กรณี String + String
```ruby
puts 'foo'.concat('bar', 'baz') # => "foobarbaz"
```
<details close>
 <summary><b>output</b></summary>
 <pre>
 foobarbaz
 </pre>
</details>

```ruby
myString = "Welcome ".concat("to ").concat("Ruby!")
puts myString
```
<details close>
 <summary><b>output</b></summary>
 <pre>
 Welcome to Ruby!
 </pre>
</details>

### กรณี String + int
  - object ที่เป็น integer จะถูกแปลงให้อยู่ในรูปรหัส unicode เช่น
     - 32 ที่ตรงกับ ช่องว่าง ในรหัส unicode
     - 1089, 1090 ที่ตรงกับ с, т ตามลำดับ ในรหัส unicode
     - 12395,12385,12399 ที่ตรงกับ に, ち, は ตามลำดับ ในรหัส unicode
   
  ```ruby
puts 'foo'.concat(32, 'bar', 32, 'baz')# => " foo bar baz" # Embeds spaces.
puts 'те'.concat(1089, 1090)# => "тест"
puts 'こん'.concat(12395, 12385, 12399)# => "こんにちは"
```
<details close>
 <summary><b>output</b></summary>
 <pre>
 foo bar baz
 тест
 こんにちは
 </pre>
</details>

## เปรียบเทียบกับภาษา C, Java และ Python

## C
การต่อสตริงบน C
### 1. ใช้เมธอด strcat
  - คล้ายกับการใช้เมธอด concat ใน Ruby
  - เมื่อต่อสตริงแล้ว สตริงต้นฉบับก็จะเปลี่ยนด้วย
  - 
  ```c
char s1[] = "Hello ";
char s2[] = "Geeks";

strcat(s1, s2);

printf("%s\n", s1); 
```

<details close>
 <summary><b>output</b></summary>
 <pre>
Hello Geeks
 </pre>
</details>




## Java
การต่อสตริงบน Java
### 1. ใช้เมธอด concat
  - คล้ายกับเมธอด cancat ใน Ruby
    ```java
      String message = "cares";
      message = message.concat("s");
      System.out.println(message);
     ```

    <details close>
       <summary><b>output</b></summary>
         <pre>
             caress
         </pre>
    </details>

     ```java
      System.out.println("to".concat("get").concat("her"));
     ```

    <details close>
       <summary><b>output</b></summary>
         <pre>
             together
         </pre>
    </details>

    ```java
      System.out.println("to".concat("get").concat("her"));
     ```

    <details close>
       <summary><b>output</b></summary>
         <pre>
             together
         </pre>
    </details>




### 2. ใช้เครื่องหมาย +
  - คล้ายกับการต่อสตริงโดยใช้เครื่องหมาย + ใน Ruby
    
    ```java
        String s1 = "Geeksfor";
        String s2 = "Geeks";
    
        s1 = s1.concat(s2);
    
        System.out.println(s1);
    ```
    <details close>
       <summary><b>output</b></summary>
         <pre>
            GeeksforGeeks
         </pre>
    </details>
    
        
    
    ```java
    String firstName = "John";
    String lastName = "Doe";
    System.out.println(firstName + " " + lastName);
    ```
    <details close>
       <summary><b>output</b></summary>
         <pre>
            John Doe
         </pre>
    </details>



## Python
การต่อสตริงบน Python
### 1. 1. ใช้เครื่องหมาย +
  - คล้ายกับการต่อสตริงโดยใช้เครื่องหมาย + ใน Ruby
    
    ```python
    head = "String Concatenation "
    tail = "is Fun in Python!"
    print(head + tail)
    ```
    <details close>
 <summary><b>output</b></summary>
 <pre>
String Concatenation is Fun in Python!
 </pre>
</details>
    

### 2. ใช้เครื่องหมาย +=

- เป็นการเพิ่ม String ใหม่ที่ตัวแปรเดิม
- สตริงก็จะถูกต่อไปเรื่อยๆ
- คล้ายกับภาษา Java

```python
word = "Py"
word += "tho"
word += "nis"
word += "ta"
print(word)
```
   <details close>
 <summary><b>output</b></summary>
 <pre>
Pythonista
 </pre>
</details>


### 3. ใช้เมธอด join
  - จากโค้ด คือ การนำช่องว่าง " " ต่อ/เชื่อมแต่ละ String ใน list

    ```python
      print(" ".join(["Hello,", "World!", "I", "am", "a", "Pythonista!"]))
    ```
<details close>
<summary><b>output</b></summary>
 <pre>
   Hello, World! I am a Pythonista!
 </pre>
</details>

### 4. ใช้  f-strings
  - การใช้คือ นำ f ไปอยู่หน้า String ที่ต้องการจะต่อ
  - ใช้ { } โดยภายใน { } เป็น String หรือ int ก็ได้

      ```python
      s1 = "Python"
      s2 = "programming"

      res = f"{s1} is a popular language for {s2}"

      print(res)
      ```
      <details close>
      <summary><b>output</b></summary>
       <pre>
          Python is a popular language for programming
      </details>


## แหล่งที่มา









