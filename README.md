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
#分享插件
[参考](http://bbs.phonegap100.com/forum.php?mod=viewthread&tid=885&highlight=phonegap%2B%E5%88%86%E4%BA%AB)  
[下载](http://dev.umeng.com/social/phonegap/share/quick-integration)
##andorid 插件调用与配置(base_plus.html)
在src目录下新建一个class[com.example.phonegap.plugin(名字任意，类名大写)]
导入
```php
import org.apache.cordova.api.CallbackContext;
import org.apache.cordova.api.CordovaPlugin;
import org.apache.cordova.api.PluginResult;
import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;
```
让你的类继承
```php
public class HelloWorld extends CordovaPlugin {
    @Override
    public boolean execute(String action, JSONArray args, CallbackContext callbackContext) throws JSONException {
        if (action.equals("echo")) {
            String message = args.getString(0);
            message = message+"你好";
            this.echo(message, callbackContext);
            return true;
        }else{
        	 callbackContext.error("失败！");
        	  return false;
        }
      
    }

    private void echo(String message, CallbackContext callbackContext) {
        if (message != null && message.length() > 0) {
            callbackContext.success(message);
        } else {
            callbackContext.error("Expected one non-empty string argument.");
        }
    }
}
```
注册插件( res/xml/)
```php
<feature name="HelloWord">
<param name="android-package" value="org.apache.cordova.helloword.HelloWord"/>
</feature>
```
