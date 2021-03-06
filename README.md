# formCheck
Form validation plug-in, used to trigger the display when the focus is lost
表单验证插件，用于在失去焦点时触发显示提示信息
###我可以做的
1.在引用插件之前，须引用jQuery文件  
2.本插件提供中文姓名 nameCheck ，电话号码 phoneCheck ，身份证号 IDCheck ，邮箱 emailCheck ，标准用户名 userNameCheck ，非空 notEmptyCheck ，密码验证 passwordCheck   
3.若未输入，默认为中文姓名验证   
4.required 若为 false 只做为空验证，但是返回的属性为相应的状态

>其中中文姓名默认为1到4位汉字。中文姓名可自定义长度验证，如下代码为2到5位  


HTML代码
```
<div class="needCheck">
	<label>姓&nbsp;&nbsp;名</label>    <input  class="demoName" type="text" name="name" value=""> <br>
        <span class="u-xg-tips"></span>
</div>
```

>其中，needCheck属性用于限定input及提示文字span的范围，需要成为他们的父元素
>u-xg-tips属性用于显示提示文字  


js代码
```
$('.demoName').formCheck(
          {
              checkModel:'nameCheck',
              nMin:2,
              nMax:5
          }
  );
```

5.用户名为大小写英文及数字6到16位

6.密码验证为6到16位 字母，数字，符号的组合，符号包括!@#$%^&*.,;'"/?+=-

###你可以做的
1.本插件可自定义验证正则表达式,错误、为空、正确的信息提示
>正确时不显示提示信息，但是会返回在在标签的属性中

js代码
```
$('.demoName').formCheck(
          {
              checkModel:'passwordCheck',
              ref:/^(\d{6})$/,
              msg:'密码输入有误',
              emptyMsg:'密码不能为空'
          }
  );
```

###重要
触发方式为失去焦点！

###如下方式可在一个对象的点击事件中触发 ---同一个提示框 

html代码
```
<div class="needCheck">
  <label>I&nbsp;&nbsp;D</label>    <input  data-xg-msg="" class="demoId" type="text" name="name" value=""> <br>
  <label>电&nbsp;&nbsp;话</label>    <input  data-xg-msg="" class="demoPhone" type="text" name="name" value=""> <br>
  <span class="u-xg-tips"></span><br>
  <a class="submitAll">确定</a>
</div>
```

###如下方式可在一个对象的点击事件中触发 ---分别有提示框   
html代码
```
<div class="needCheck">
  <label>电&nbsp;&nbsp;话</label>    <input  data-xg-msg="" class="demoPhone" type="text" name="name" value=""> <br>
  <span class="u-xg-tips"></span><br>
</div>
<div class="needCheck">
  <label>I&nbsp;&nbsp;D</label>    <input  data-xg-msg="" class="demoId" type="text" name="name" value=""> <br>
  <span class="u-xg-tips"></span><br>
</div>
<div class="needCheck">
  <a class="submitAll">确定</a>
</div>
```
js代码相同为  

```
$('.demoPhone').formCheck(
   {
      checkModel:'phoneCheck',
      msg:'手机为13位位数字',
      emptyMsg:'手机号不能为空'
   }
);
$('.demoId').formCheck(
   {
      checkModel:'IDCheck',
      msg:'ID为18位位数字',
      emptyMsg:'ID不能为空'
   }
);
```

提示框会显示第一个未通过的信息  

```
$(this).get(0).resultBool
```
中保存该项是否通过的布尔值

###重要
暂不支持同一页面有两个确认按钮
>更改提交按钮的选择方式即可，下一个版本更新

