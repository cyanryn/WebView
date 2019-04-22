# WebView
自定义浏览器

##### AndroidManifest.xml
```
<activity android:name=".MyWebView">
			<intent-filter>
				<action android:name="android.intent.action.MAIN" />
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <data android:scheme="http"/>
                <category android:name="android.intent.category.LAUNCHER" />
			</intent-filter>
        </activity>
```

##### MyWebView.java
```
private void initView() {
        webView = findViewById(R.id.myWebView);
        url = getIntent().getData().toString();
    }

    private void setWebView() {

        WebSettings webSettings = webView.getSettings();
        webSettings.setJavaScriptEnabled(true);
        webSettings.setSupportZoom(true);
        webView.loadUrl(url);
        webView.setWebViewClient(new WebViewClient(){
            @Override
            public boolean shouldOverrideUrlLoading(WebView view, String url) {
                webView.loadUrl(url);
                return true;
            }
        });

    }
```
