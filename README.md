# QZBaseWebVCDemo

WebView基类，>iOS8使用WKWebView，否则使用UIWebView,都自带进度条 


/**
*  系统大于ios8 使用wkwebView加载页面
*  否则使用uiwebView加载页面
*/

@interface QZBaseWebVC : UIViewController
/** 子类类型转换*/
@property (nonatomic,weak) id webView;

@property (nonatomic,copy) NSString *url;

@property (nonatomic,strong) NJKWebViewProgressView *progressView;

@property (nonatomic,strong) NJKWebViewProgress *progressProxy;

@property (nonatomic,assign) double timeOut;
/**
*  统一wk ui加载状态代理方法，二合一
*/
@property (nonatomic,copy) void(^startLoadBlock)(id webView);
@property (nonatomic,copy) void(^finishLoadBlock)(id webView);
@property (nonatomic,copy) void(^failLoadBlock)(id webView);

- (void)hideProgressView;

- (void)loadRequest:(NSString *)url;

- (void)scrollToTop;
/**
*  方法内部判断是什么view
*  在外部直接传入js即可
*/
- (void)evaluateJavaScript:(NSString *)javaScript;
