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
