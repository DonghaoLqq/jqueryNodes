## 一  、jQuery 如何获取元素
###   基础选择器
```javascript
 $("选择器") // 里面选择器直接写css选择器即可，但是要加引号
```
1. id选择器：$("#id")	   获取指定id元素
2. 全选选择器：$("*")	匹配所有元素
3. 类选择器：$(".class")	   获取同一类class元素
4. 标签选择器：$("div")	获取同一类标签的所有元素
5. 并集选择器：$("div,p,li")	获取多个元素
6. 交集选择器：$("li.current")	交集元素
7. 子代选择器：$("ul>li")	使用>号，获取亲儿子层级的元素，不会获取孙子层级元素
8. 后代选择器：	$("ul li")	使用空格，代表后代选择器，获取ul下所有li元素，包括孙子层级

###  筛选选择器
1. :first选择器：	 $("li:first")	获取第一个li元素
2. :last选择器：	$("li:last")	获取最后一个li元素
3. :eq(index)选择器：	$("li:eq(2)")	获取到的li元素中，选择索引号为2的元素，索引号从0开始
4. :odd选择器：	$("li:odd")	获取到的li元素中，选择索引号为奇数的元素
5. :even选择器：	$("li:even")	获取到的li元素中，选择索引号为偶数的元素

### 筛选方法
1. parent()：	$("li").parent()	查找父级
2. children(selector)：		$("ul").children("li")	相当于$("ul>li")，最近一级（亲儿子）
3. find(selector)：		$("ul").find("li")	相当于$("ul li")，后代选择器
4. siblings(selector)：		$(".first").siblings("li")	查找兄弟节点，不包括自己本身
5. nextAll([expr])：		$(".first").nextAll()	查找当前元素之后所有的同辈元素
6. prevtAll([expr])：		$(".last").prevAll()	查找当前元素之前所有的同辈元素
7. hasClass（class)：	$('div').hasClass("nav")	检查当前的元素是否含有某个特定的类，如果有则返回true
8. eq(index)：		$("li").eq(2)	相当于$("li:eq(2)"),index从0开始

## 二、jQuery 的链式操作是怎样的（链式编程）

``` javascript
$(this).css('color','red').siblings().css('color','')
```
## 三、 jQuery 如何创建元素
``` javascript
$(function(){
   // 1. 创建元素
   var li = $("<li>我是后来创建的li</li>");
   // 2. 添加元素
   // (1)内部添加
   $("ul").prepent(li);    // 内部添加并且放到内容最前面
   $("ul").append(li);    // 内部添加并且放到内容最后面
    // (2)外部添加
    var div = $("<div>我是后妈生的</div>");
    $(".test").after(div);
    $(".test").before(div);
})
```
## 四、 jQuery 如何移动元素

   ### 元素的操作：移动

   提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。

   假定我们选中了一个div元素，需要把它移动到p元素后面。

   第一种方法是使用[.insertAfter()](https://api.jquery.com/insertAfter/)，把div元素移动p元素后面：

   > 　　$('div').insertAfter($('p'));

   第二种方法是使用[.after()](https://api.jquery.com/after/)，把p元素加到div元素前面：

   > 　　$('p').after($('div'));

   表面上看，这两种方法的效果是一样的，唯一的不同似乎只是操作视角的不同。但是实际上，它们有一个重大差别，那就是返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素。你可以根据需要，选择到底使用哪一种方法。

   使用这种模式的操作方法，一共有四对：

   > 　　[.insertAfter()](https://api.jquery.com/insertAfter/)和[.after()](https://api.jquery.com/after/)：在现存元素的外部，从后面插入元素
   >
   > 　　[.insertBefore()](https://api.jquery.com/insertBefore/)和[.before()](https://api.jquery.com/before)：在现存元素的外部，从前面插入元素
   >
   > 　　[.appendTo()](https://api.jquery.com/appendTo/)和[.append()](https://api.jquery.com/append)：在现存元素的内部，从后面插入元素
   >
   > 　　[.prependTo()](https://api.jquery.com/prependTo/)和[.prepend()](https://api.jquery.com/prepend)：在现存元素的内部，从前面插入元素

## jQuery 如何修改元素的属性

### 1. 操作CSS方法
   jQuery可以使用css方法修改简单元素样式，也可以操作类，修改多个样式

   （1）参数只写属性名，则是返回属性值
   ```javascript
   $(this).css("color");
   ```
   （2）参数是属性名，属性值，逗号分隔，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引导。
   ```javascript
   $(this).css("color","red");
   ```
   （3）参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开，属性可以不用加引号
   ```javascript
   $(this).css("color":"red","font-size":"20px");
   ```
   ### 2. 操作样式之CSS方法
   ``` javascript
    $(function(){
         console.log($("div").css("width"));
         $("div").css({
            width:400,
            height:400,
            backgroundColor:red
         })
      })
   ```

### 3. 设置类样式方法
作用等同于以前的classList,可以操作类样式，注意操作类里面的参数不要加点

（1）添加类
   ``` javascript
      $("div").addClass("current");
   ```
（2）移出类
   ``` javascript
       $("div").removeClass("current");
   ```
（3）切换类
   ``` javascript 
       $("div").toggleClass("current");
   ```
   