# cloudifyimage-android-lib
This library is for uploading the images from android applications to the CloudfyImage server

## How to use
Add gradle dependancy

```java
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}
```

```java
dependencies {
	compile 'com.github.cloudifyimage:cloudifyimage-android-lib:0.0.1'
}
```

Java Utility
```java
new CloudifyImageUtil()
	.addServerUrl({CLOUDIFY_SERVER_URL})
	.addCredentials({YOUR_API_KEY}, {YOUR_API_SECRET})
	.send("Rahul", path);
```

Adding Custom Listener:
- Create a listener class implementing the `CloudifyImageListener` interface
```java
class MyListener implements CloudifyImageListener {

	@Override
	public void onSuccess(String response) {
		// code
	}

	@Override
	public void onFailure(String errorMessage) {
		// code
	}
}
```

- Before calling the `send()` method, call the `addListener(new MyListener())`

Adding Custom Progress-Dialog:
- Create a custom ProgressDialog class object
- Pass the object to the `addProgressDialog(customProgressDialog)` method

###Example
```java
new CloudifyImageUtil()
	.addServerUrl({CLOUDIFY_SERVER_URL})
	.addCredentials({YOUR_API_KEY}, {YOUR_API_SECRET})
	.addListener(new MyListener())
	.addProgressDialog(pDialog)
	.send({YOUR_COLLECTION_NAME}, {ABSOLUTE_PATH_OF_IMAGE});
```

