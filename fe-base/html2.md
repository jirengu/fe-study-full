# HTML 表单

我们平时填写的纸质表单一样，HTML 表单用于搜集不同类型的用户输入

表单是一个包含表单元素的区域
表单元素是允许用户在表单中（比如：文本域、下拉列表、单选框、复选框等等）输入信息的元素
```
	<form action="xxx.php" method="post">
		<h3>输入框</h3>
		<label for="input_username">用户名：</label> <input id="input_username" name="username" type="text" placeholder="输入用户名" autofocus/>
		<br/>
		<label for="input_pass">密码：</label> <input id="input_pass" name="password" type="password" placeholder="输入密码"/>
		<br/><br/>

		<h3>单选框</h3>
		<label for="ck1">ra1：</label><input type="radio" id="ra1" name="ra" value="1" />
		<br/>
		<label for="ra2">ra2：</label><input type="radio" id="ra2" name="ra" value="2" />
		<br/>
		<label for="ra3">ra3：</label><input type="radio" id="ra3" name="ra" value="3" />
		<br/>
		<label for="ra4">ra4：</label><input type="radio" id="ra4" name="ra" value="4" />
		<br/><br/>
		<label for="ck5">ra5：</label><input type="radio" id="ra5" name="radio" value="1" />
		<br/>
		<label for="ra6">ra6：</label><input type="radio" id="ra6" name="radio" value="2" />
		<br/>
		<label for="ra7">ra7：</label><input type="radio" id="ra7" name="radio" value="3" checked="checked" />
		<br/>
		<label for="ra8">ra8：</label><input type="radio" id="ra8" name="radio" value="4" />
		<br/><br/>


		<h3>复选框</h3>
		<label for="ck1">CK1：</label><input type="checkbox" id="ck1" name="ck" value="1" />
		<br/>
		<label for="ck2">CK2：</label><input type="checkbox" id="ck2" name="ck" value="2" checked />
		<br/>
		<label for="ck3">CK3：</label><input type="checkbox" id="ck3" name="ck" value="3" />
		<br/>
		<label for="ck4">CK4：</label><input type="checkbox" id="ck4" name="ck" value="4" />
		<br/><br/>

		<h3>File</h3>
		<input type="file" accept="image/png, image/jpeg"/>
		<br/><br/>

		<h3>隐藏域</h3>
		<input type="hidden" value="xxx" />
		<br/><br/>


		<h3>下拉菜单</h3>
		<select id="input_select">
			<option value="1">1</option>
			<option value="2" selected="selected">2</option>
			<option value="3">3</option>
			<option value="4">4</option>
		</select>
		<br/><br/>

		<h3>多行文本</h3>
		<textarea cols="60" rows="5">123</textarea>
		<br/><br/>

		<input type="button" value="Buttom" /> &nbsp;&nbsp;
		<input type="submit" value="Submit" />  &nbsp;&nbsp;
		<input type="reset" value="Reset" />

	</form>
```
<form action="xxx.php" method="get">
	<h3>输入框</h3>
	<label for="input_username">用户名：</label> <input id="input_username" name="username" type="text" placeholder="输入用户名" autofocus/>
	<br/>
	<label for="input_pass">密码：</label> <input id="input_pass" name="password" type="password" placeholder="输入密码"/>
	<br/><br/>
	<h3>单选框</h3>
	<label for="ck1">ra1：</label><input type="radio" id="ra1" name="ra" value="1" />
	<br/>
	<label for="ra2">ra2：</label><input type="radio" id="ra2" name="ra" value="2" />
	<br/>
	<label for="ra3">ra3：</label><input type="radio" id="ra3" name="ra" value="3" />
	<br/>
	<label for="ra4">ra4：</label><input type="radio" id="ra4" name="ra" value="4" />
	<br/><br/>
	<label for="ck5">ra5：</label><input type="radio" id="ra5" name="radio" value="1" />
	<br/>
	<label for="ra6">ra6：</label><input type="radio" id="ra6" name="radio" value="2" />
	<br/>
	<label for="ra7">ra7：</label><input type="radio" id="ra7" name="radio" value="3" checked="checked" />
	<br/>
	<label for="ra8">ra8：</label><input type="radio" id="ra8" name="radio" value="4" />
	<br/><br/>
	<h3>复选框</h3>
	<label for="ck1">CK1：</label><input type="checkbox" id="ck1" name="ck" value="1" />
	<br/>
	<label for="ck2">CK2：</label><input type="checkbox" id="ck2" name="ck" value="2" checked />
	<br/>
	<label for="ck3">CK3：</label><input type="checkbox" id="ck3" name="ck" value="3" />
	<br/>
	<label for="ck4">CK4：</label><input type="checkbox" id="ck4" name="ck" value="4" />
	<br/><br/>
	<h3>File</h3>
	<input type="file" accept="image/png, image/jpeg"/>
	<br/><br/>
	<h3>隐藏域</h3>
	<input type="hidden" value="xxx" />
	<br/><br/>
	<h3>下拉菜单</h3>
	<select id="input_select">
		<option value="1">1</option>
		<option value="2" selected="selected">2</option>
		<option value="3">3</option>
		<option value="4">4</option>
	</select>
	<br/><br/>
	<h3>多行文本</h3>
	<textarea cols="60" rows="5">123</textarea>
	<br/><br/>
	<input type="button" value="Buttom" /> &nbsp;&nbsp;
	<input type="submit" value="Submit" />  &nbsp;&nbsp;
	<input type="reset" value="Reset" />
</form>
## form

form标签是表单的外壳，主要有四个属性

1. action： 表单提交的地址
2. method：提交保单的方法
3. target：在何处打开action
4. enctype:
	* application/x-www-form-urlencoded：在发送前编码所有字符（默认）
	* text/plain：空格转换为 "+" 加号，但不对特殊字符编码
	* multipart/form-data：使用包含文件上传控件的表单时，必须使用该值

## type="password"

输入内容自动变成圆点

## type="checkbox"

靠`name`属性分组，提交到后端的时候被选中的value是以`,`分割的一个字符串，通过name属性获得

## type="file"
accept 为接受上传的文件类型
## type="select"
后端以select标签的name获取选中的option的value

## get vs post
- 使用场景
- 安全性
- 长度限制


