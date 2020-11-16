### 编写 MANIFEST.MF 文件时的注意事项：
说明：一般编写 MANIFEST.MF 文件只需要用到 Manifest-Version（MF文件版本号）、Main-Class（包含main方法的类）、Class-Path（执行这个jar包时的ClassPath，第三方依赖),比如以下的例子：  
```
Manifest-Version: 1.0 
Main-Class: test.Main 
Class-Path: ./ ./lib/commons-collections-3.2.jar ./lib/commons-dbcp-1.2.2.jar ./lib/commons-lang-2.3.jar ./lib/commons-logging-1.1.jar 

```
#### 以下是需要注意的各个要点： 
1. 最后一样一定要回车，空一行，不然无法识别最后一行的配置。
2. Manifest-Version、Main-Class和Class-Path后面跟着一个英文的冒号，冒号后面必须跟着一个空格，然后才是版本号、类和ClassPath。 
3. Class-Path中的各项应使用空格分隔，不是逗号或分号。 
4. Class-Path中如果有很多项，写成一行打包的时候会报错line too long，这时需要把Class-Path分多行写。注意：从第二行开始，必须以两个空格开头，三个以上我没试过，不过不用空格开头和一个空格开头都是不行的，我已经试过了。 
5. Class-Path写完之后最后一定要有一个空行。 
6. jar包内有些配置文件想放在jar包外面，比如文件config.properties：如果这个文件是以路径方式载入的，比如new file("./config/config.properties")，那么将config.properties放在jar包相同目录下的config目录下即可，也就是说“./”路径等价于jar包所在目录；如果这个文件是以ClassPath下的文件这种方式载入的，比如在Spring中载入classpath:config.properties，则在MF文件的配置文件的ClassPath中添加“./”，然后将这个配置文件与jar包放在同一个目录即可，当然也可以在MF文件的配置文件的ClassPath中添加“./config/”，然后把配置文件都放在jar包相同目录下的config目录下。

参考于[MANIFEST.MF文件详解](https://www.cnblogs.com/Gandy/p/7290069.html)
