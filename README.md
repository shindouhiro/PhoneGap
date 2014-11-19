PhoneGap
========

#自定义弹窗(alert.html)
```php
// 等待加载PhoneGap
	document.addEventListener("deviceready", onDeviceReady, false); 
	// PhoneGap加载完毕
	function onDeviceReady() {
		//使用alert()方法显示一个提示
	}
	// 警告对话框被忽视
	function alertDismissed() {
		// 进行处理
	}
	// 显示一个定制的警告框
	function showAlert() {
		navigator.notification.alert(
			'这是使用notification.alert()方法显示警告',           // 显示信息
			alertDismissed,								 // 警告被忽视的回调函数
			'这是一个标题',								 // 标题
			'我就不说这个按钮是可以自定义的'                // 按钮名称
		);
	}
```
#确认弹窗(confirm.html)
```php
// 等待加载PhoneGap
	document.addEventListener("deviceready", onDeviceReady, false); 
	// PhoneGap加载完毕
	function onDeviceReady() {
		//使用alert()方法显示一个提示
	}
	// 警告对话框被忽视
	function onConfirm() {
		// 进行处理
		alert("点击按钮后运行回调函数");
	}
	// 显示一个定制的警告框
	function showConfirm() {
		 navigator.notification.confirm(
			'这是使用notification.confirm()方法显示对话框',  	 // 显示信息
			onConfirm,								 // 警告被忽视的回调函数
			'这是一个标题',								 // 标题
			'这个按钮也是可以自定义的'             		 // 按钮名称
		);
	}
```

#传递变量弹窗(prompt.html)
```php
// 等待加载PhoneGap
	document.addEventListener("deviceready", onDeviceReady, false); 
	// PhoneGap加载完毕
	function onDeviceReady() {
		//使用alert()方法显示一个提示
	}
	//从对话框中获得下一步操作的数据
	function onPrompt() {
		// result是从Prompt对话框中获取的值，buttonIndex存放被点击的按钮的索引
		if(results.buttonIndex==0){
			//results.input1中存放的是编辑框中输入的值
			alert("你要了"+results.input1+"杯咖啡");
		}
	}
	// 显示一个定制的对话框
	function showPrompt() {
		 navigator.notification.prompt(
			'请问你需要喝杯咖啡么？',                    // 显示信息
			onPrompt,								 // 警告被忽视的回调函数
			'将想要的数量输入在对话框内',				 // 标题
			['要','不要']                                  // 按钮名称
		);
	}
```
