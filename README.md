<div class="container">

<div class="row">

<div class="span9">

<section id="huanxing1">

<div class="page-header">

# 外部唤醒手厅后打开h5页面(非免登)

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">//android chrome
var huanxing_chrome = 'intent://platformapi/startapp?addr=com.businesshall.activity.WebviewActivity&type=url_dna_'+url_h5+'_dna_'+title_h5+'_dna_'+params+'#Intent;package=com.example.businesshall;scheme=zjmobile;end';
//android 其他
var huanxing_other = 'zjmobile://platformapi/startapp?addr=com.businesshall.activity.WebviewActivity&type=url_dna_'+url_h5+'_dna_'+title_h5+'_dna_'+params;
//ios
var huanxing_ios = 'zjmobilesjyyt://'+title_h5_un+'_value_'+url_h5+'_value_'+params;
    </pre>

### 说明：

必须参数：目标网址url;目标网址title;如目标网址包含自带参数，则需要放到params里。具体请参考demo源码。

### demo：

[demo1](http://app.m.zj.chinamobile.com/zjweb/sjyyt/hdshare/feixiangtc.html)![](images/demo1.jpg)

<div class="page-header">

# 唤醒手厅后打开native页面(非免登)

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">//android chrome
var huanxing_chrome = 'intent://platformapi/startapp?addr=com.businesshall.activity.QueryAccountBillActivity';
//android 其他
var huanxing_other = 'zjmobile://platformapi/startapp?addr=com.businesshall.activity.QueryAccountBillActivity';
//ios
var huanxing_ios = 'zjmobilesjyyt://RootViewController';
    </pre>

### 说明：参考demo

替换唤醒码中对应的类名，则唤醒至各个native页面；目前版本（安卓ok，ios：2.3.2）中：ios只能唤醒到首页。

### demo：

[demo2](http://app.m.zj.chinamobile.com/zjweb/sjyyt/hdshare/zhangdancx.html) ![](images/demo2.jpg)
[demo3:安卓外部唤醒到具体native页面的demo](http://app.m.zj.chinamobile.com/zjweb/sjyyt/test/h5huanxingtest.html) ![](images/demo3.jpg)[demo4:安卓/ios 唤醒到首页](http://www.hssmwd.com/uploads/hdshare/index.html)![](images/demo_index.jpg)</section>

<section id="huanxing2">

<div class="page-header">

# 外部唤醒手厅后打开h5页面(免登)

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">//android chrome
var huanxing_chrome = 'intent://platformapi/startapp?addr=com.businesshall.activity.WebviewActivity&token='+token+'&type=url_dna_'+url_h5+'_dna_'+title_h5+'_dna_'+params_an+'#Intent;package=com.example.businesshall;scheme=zjmobile;end';
//android 其他
var huanxing_other = 'zjmobile://platformapi/startapp?addr=com.businesshall.activity.WebviewActivity&token='+token+'&type=url_dna_'+url_h5+'_dna_'+title_h5+'_dna_'+params_an;
//ios
var huanxing_ios = 'zjmobilesjyyt://'+title_h5_un+'_value_'+url_h5+'_value_'+params_ios+'_value_token='+token;//ios唤醒至h5后带的参数位数有限制。第四位放advert；第五位放token
    </pre>

### 说明：

对比非免登方式，多了token值。

### demo：

[demo4](http://www.hssmwd.com/uploads/mianmi_h5.html)![](images/demo4.jpg)

<div class="page-header">

# 唤醒手厅后打开native页面(免登)

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">gonativeAn="zjmobile://platformapi/startapp?addr=com.businesshall.activity.PaymentActivity&token=" gonativeIos="zjmobilesjyyt://Main_separator_RechargeViewController_separator_token="; //ios唤醒至native后带的参数位数无限制。
    </pre>

### 说明：

对比非免登方式，多了token值;对于未来新版ios，抛弃老版本唤醒问题的bug，引入分隔符：_separator_ ，达到ios也能唤醒具体native的功能

### demo：

[demo5](http://www.hssmwd.com/uploads/mianmi_native.html)![](images/demo5.jpg)</section>

<section id="tiaozhuan">

<div class="page-header">

# 内部h5页面跳转到native

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">v_ios="RechargeViewController" v_and="window.stub.jsMethod('com.businesshall.activity.PaymentActivity','1','');"
注：ios: 内部跳转并未涉及到 & _separator_分隔符问题，都是用&。
android：安卓跳转包名和下面的外部唤醒的包名相同，
第二个参数固定数字：
1常规页面 
2虚拟网
3 4G自选
4微信微博短信等分享渠道相关 
5通讯录相关
6支付页面
7检查更新 
第三个参数默认为空，几个第三个参数不为空的例子： window.stub.jsMethod('com.businesshall.activity.OrderActivity','1','marketid&8010020140611001' 跳转到4G飞享套餐（各个业务页更改相应marketid）
    </pre>

### 说明：

跳转到其他页面，替换对应类名即可，具体请参考demo源码第53行。

### demo：

[demo6](http://app.m.zj.chinamobile.com/zjweb/sjyyt/test/h5-ability.html)![](images/demo6.jpg)</section>

<section id="banben">

<div class="page-header">

# 获取版本号

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">引入js：../js/zjversion.js
页面：var versionid = ZJ.Version.versionid();//定义全局版本号versionid
注：直接调用时安卓可获取版本号 ios为undefined；解决方案：
原本直接调用的test()改成setTimeout(function(){test();},0); 
    </pre>

### 说明：

### demo：

[demo7](http://app.m.zj.chinamobile.com/zjweb/sjyytv3/found/index.html) ![](images/demo7_new.jpg)[demo7_1](http://www.nczzt.com/uploads/version2.html)![](images/demo7_1.jpg)</section>

<section id="isApp">

<div class="page-header">

# 通过获取版本号来判断当前环境是否是手厅:经过验证在ios的safari浏览器中会先弹框报错，此方法不完善。

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">var versionid = ZJ.Version.versionid();//定义全局版本号versionid

setTimeout(function(){isApp();},0); 

function isApp(){
  if(versionid){
    alert('是手厅')
  }else{
    alert('不是手厅')   
  }
}
    </pre>

### 说明：

### demo：

[demo7](http://www.nczzt.com/uploads/version2.html)![](images/demo18.jpg)

<div class="page-header">

# 直接判断是否是手厅环境和版本号新方法 20160523

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">var ua = navigator.userAgent.toLowerCase();
var versionid = '';//手厅版本号

if(is_app()){
  alert('是手厅')
  var versionid = ua.match(/sjyyt\/(\S*)/)[1];//获取版本号
  alert('版本号是'+versionid)
}else{
  alert('不是手厅')
}

    </pre>

### 说明：

打开页面同时判断是否手厅 要求安卓>3.0.1 ios>3.0.0 老版本无效 兼容思路可以参考分享功能：若无法使用请升级客户端 引导用户使用最新客户端。

### demo：

[demo7](http://www.nczzt.com/uploads/isapp.html)![](images/demo19.jpg)</section>

<section id="share">

<div class="page-header">

# 分享能力（朋友 朋友圈 短信 微信） 20160512 新增qq和qq空间和微博v2 手厅版本要求ios>3.0.0 安卓>3.0.1 
20160613 新增短信默认入参号码 1个或者多个 手厅版本要求ios>=3.1.0 安卓>=3.1.0

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">参数名参  数填写规范 参数说明
imgUrl_sina   图片链接  新浪微博配图
content_sina  字符串 新浪微博分享的文案
title_weixin  字符串 微信和朋友圈的标题
imgUrl_weixin 图片链接（300*300不得超过32k）  微信和朋友圈的配图
content_weixin  字符串 微信和朋友圈的内容
link_weixin 字符串 微信和朋友圈的链接
content_message 字符串 短信的内容

num_message = [13868019995,13456868493];//短信分享的默认手机号
var title_qq = '';//qq和qq空间的title
var imgUrl_qq = '';//qq和qq空间的图片
var content_qq = '';//qq和qq空间的内容
var link_qq = '';//qq和qq空间的链接

微博v2的方法解决了ios中 入参的网址无法带参数的问题。

参考 http://www.nczzt.com/uploads/chongzhi/js/clicksharev2.js

    </pre>

### 说明：参考demo中的分享功能源码

### demo：

[demo8](http://www.nczzt.com/uploads/chongzhi/index.html)![](images/demo8_2.jpg)</section>

<section id="txl">

<div class="page-header">

# 通讯录（单条信息、所有联系人信息）

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">if(is_android()){ 
  window.stub.jsMethod('contactlist','5','');
}
if(is_iphone()){ 
  getcontactinfo_ios();
}
    </pre>

### 说明：参考demo中的源码31行

### demo：

[demo6](http://app.m.zj.chinamobile.com/zjweb/sjyyt/test/h5-ability.html)![](images/demo6.jpg)</section>

<section id="login">

<div class="page-header">

# H5页面点击调用登录框功能

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">if(is_android()){
  window.stub.gotowebview(islogin,isnative,gotoUrl,urlInfo,mytitle,isgesture);//第一个参数：0为默认正常情况 不需要登录 1为网址无参 需要登录 2为网址有参session过期; 第二个参数： 1 native 2 h5  最后一个1是需要手势，0则不需要手势。
}
if(is_iphone()){
  gotowebview_ios(mytitle,gotoUrl,urlInfo,islogin,isgesture);
}
    </pre>

### 说明：参考demo

### demo：

[demo9](http://app.m.zj.chinamobile.com/zjweb/sjyyt/test/timeouttest2.html)![](images/demo9.jpg)</section>

<section id="relogin">

<div class="page-header">

# H5页面内部跳转js方法20160511更新

</div>

### 核心代码

<pre class="prettyprint linenums prettyprinted">说明：使用前加是否是手厅判断（根据具体业务场景而定 仅仅是手厅则不用 如有外部渠道则必须）：
var versionid = ZJ.Version.versionid();//定义全局版本号versionid

$('.test').click(function(){
  if(versionid){
    alert('是手厅 跳转方式可用goweb方法')
  }else{
    alert('不是手厅 跳转方式用常规js跳转')   
  }
})
测试demo： http://www.nczzt.com/uploads/version.html 
仅H5：
  urlInfo = 'channel='+channel+'&version='+version;//url参数
  gotoUrl = gUrl+"sjyytv3/found/found_list.html";//h5跳转地址
  isnative = 2;//2为h5 1为native
  mytitle = '发现活动';
  islogin = 1;//1需要登录 0不需要
  isgesture = 0;//1需要手势 0不需要手势
  goweb(islogin,isgesture,gotoUrl,isnative,mytitle,urlInfo);

仅native特例：
  3期流量专区跳转至魔品应用市场详情页JS方法:(仅安卓)
  版本：3.0.0&3.0.1
  urlInfo = 'appkey='+appkey;//魔品首页:urlInfo = ''; 详情页为urlInfo = 'appkey=123',其中123为应用编号
  gotoUrl = 'MopoteManager';
  isnative = 1;//2为h5 1为native
  mytitle = '';
  islogin = 1;//1需要登录 0不需要
  isgesture = 0;//1需要手势 0不需要手势
  goweb(islogin,isgesture,gotoUrl,isnative,mytitle,urlInfo);
  版本：>=3.0.2
  此方法兼容3.0.0&3.0.1
  urlInfo = NO_ID+'='+appkey;//魔品首页:urlInfo = '';//需求变更 =两边 左边是新参数NO_ID的值右边是appkey的值
  gotoUrl = 'MopoteManager';
  isnative = 1;//2为h5 1为native
  mytitle = '';
  islogin = 1;//1需要登录 0不需要
  isgesture = 0;//1需要手势 0不需要手势
  goweb(islogin,isgesture,gotoUrl,isnative,mytitle,urlInfo);

兼容H5和native：
//跳转参数列表
var urlInfo = '';//url参数
var gotoUrl = '';//h5跳转地址
var native_args = '';//安卓包的参数
var storyboardname = '';//ios故事版
var isnative = '';//是否native 1是 2是h5  int
var mytitle = '';//标题
var islogin = '';//是否需要登录0不需要 1需要 int
var isgesture = '';//是否需要手势密码，0不需要 1需要 int
var viewname = '';//包名（ios/安卓）
var androidNative = '';//安卓包名
//native：安卓: androidNative+&+native_args（如果有native_args）; ios: storyboardname+&+viewname（如果有viewname）

//充值 native
$(".jgg1").bind('click',function(){
  urlInfo = '';
  gotoUrl = '';
  native_args = '';
  storyboardname = 'Main';
  isnative = 1;//type:1native 2web
  mytitle = '充值';
  islogin = 1;
  isgesture = 0;
  viewname = 'RechargeViewController';
  androidNative = 'com.businesshall.activity.PaymentActivity';
  goweb_rdy(urlInfo,gotoUrl,native_args,storyboardname,isnative,mytitle,islogin,isgesture,viewname,androidNative);

})
//4G飞享套餐
$(".jgg4").bind('click',function(){
  urlInfo = 'marketid=8010020140611001&type=1';
  gotoUrl = 'http://app.m.zj.chinamobile.com/zjweb/sjyyt/handle.html';
  native_args = '';
  storyboardname = '';
  isnative = 2;//type:1native 2web
  mytitle = '4G飞享套餐';
  islogin = 1;
  isgesture = 0;
  viewname = '';
  androidNative = '';
  goweb_rdy(urlInfo,gotoUrl,native_args,storyboardname,isnative,mytitle,islogin,isgesture,viewname,androidNative);

})

function goweb_rdy(urlInfo, gotoUrl, native_args, storyboardname, isnative, mytitle, islogin, isgesture, viewname, androidNative) {
    if (isnative == 2) { // 1 native 2 h5  
        goweb(islogin, isgesture, gotoUrl, isnative, mytitle, urlInfo);
    } else { //native：安卓: viewname+&+native_args（如果有native_args）; ios: storyboardname+&+viewname（如果有viewname）
        if (is_android()) {
            var andr = "";
            if (native_args == "") {
                andr = androidNative;
            } else {
                andr = androidNative;
                urlInfo = native_args;//20160517修改  安卓的包名参数也放到urlInfo里。
            }
            goweb(islogin, isgesture, andr, isnative, mytitle, urlInfo);
        }
        if (is_iphone()) {
            var ios = "";
            if (storyboardname == "") {
                ios = viewname;
            } else {
                ios = storyboardname + "&" + viewname;
            }
            goweb(islogin, isgesture, ios, isnative, mytitle, urlInfo);
        }
    }
}

function goweb(islogin,isgesture,gotoUrl,isnative,mytitle,urlInfo){
  if(is_android()){
    window.stub.gotowebview(islogin,isnative,gotoUrl,urlInfo,mytitle,isgesture);//第一个参数：0为默认正常情况 不需要登录 1为网址无参 需要登录 2为网址有参session过期; 第二个参数： 1 native 2 h5  最后一个1是需要手势，0则不需要手势。
  }
  if(is_iphone()){
    gotowebview_ios(mytitle,gotoUrl,urlInfo,islogin,isgesture);
  }
}
function gotowebview_ios(mytitle,gotoUrl,urlInfo,islogin,isgesture){
  //var json ='{"function":"webloginAndJump:","targetLink":"'+gotoUrl+'","webArg":"'+urlInfo+'","title":"'+mytitle+'"}';
  var json ='{"function":"webloginAndJump:","title":"'+mytitle+'","targetLink":"'+gotoUrl+'","webArg":"'+urlInfo+'","needLogin":"'+islogin+'","needGesture":"'+isgesture+'"}';
    webPostnotification(json);
}
function webPostnotification(func){  
    document.location ="webkitpostnotification:"+func;
}
//判断环境
function is_android(){
    if(ua.match(/android/i)=="android"&&ua.match(/iemobile/i)!="iemobile") {
         return true;
    } else {
         return false;
    }
}
function is_iphone(){
    if(ua.match(/iphone/i)=="iphone"&&ua.match(/iemobile/i)!="iemobile") {
         return true;
    } else {
         return false;
   }
}
    </pre>

### 说明：参考demo

发现二级页 ： http://app.m.zj.chinamobile.com/zjweb/sjyytv3/found/found_list.html

### demo：

[发现二级页](http://app.m.zj.chinamobile.com/zjweb/sjyytv3/found/found_list.html) ![](images/demo15.jpg)
20160510 demo： http://www.hssmwd.com/uploads/zjjh.html
 [各种混合跳转1（测试包扫一扫）](http://www.hssmwd.com/uploads/zjjh.html) ![](images/demo16.jpg)
20160517 demo：http://www.nczzt.com/uploads/tiaozhuandemo/index.html
 [各种混合跳转2](http://www.nczzt.com/uploads/tiaozhuandemo/index.html)![](images/demo17.jpg)</section>

<section id="huanxing3">

<div class="page-header">

# 外部唤醒手厅(非免登 增加可配置启动广告)

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">版本要求:ios>2.3.2 ; 安卓>2.1.4
在唤醒中间页基础之上加入参:advert=0　启动app时有广告页；advert=1　启动app时无广告页
    </pre>

### 说明：参考demo

### demo：

[唤醒到H5的demo11](http://www.hssmwd.com/uploads/advert_h5.html) ![](images/demo11.jpg)[唤醒到native的demo12](http://www.hssmwd.com/uploads/advert_native.html)![](images/demo12.jpg)</section>

<section id="baoming">

<div class="page-header">

# 安卓/ios 对应包名

</div>

### 安卓

<pre class="prettyprint linenums prettyprinted">
'addr=com.businesshall.enterance.NewMainActivity'2.0以上版本首页
'addr=com.businesshall.activity.MainActivity' 2.0以下版本首页   

'addr=com.businesshall.activity.PaymentActivity'充值页面
'addr=com.chinamobile.flow.activity.FlowMainActivity'流量专区
'addr=com.chinamobile.flow.activity.FlowOrderActivity'流量订购
'addr=com.chinamobile.flow.activity.FlowStatMonthActivity'每月流量消耗统计
'addr=com.chinamobile.flow.activity.FlowBillActivity'流量账单
'addr=com.businesshall.activity.FamilyNetworkActivity'亲情网
'addr=com.businesshall.activity.QueryAccountBillActivity'账单查询（我的账单）
'addr=com.businesshall.activity.ChargeRecordActivity'充值记录
'addr=com.businesshall.activity.ScoreQueryNewActivity'我的积分(积分兑换)
'addr=com.businesshall.activity.FlowPackageQueryActivity'套餐余量
'addr=com.businesshall.activity.SimCardActivity'Sim卡备份
'addr=com.businesshall.activity.SetActivity'设置
'addr=com.businesshall.activity.FAQActivity'常见问题
'addr=com.businesshall.activity.AboutUsActivity'关于我们
'addr=com.businesshall.activity.FeedBackActivity'意见反馈
'addr=com.businesshall.activity.MoreActivity'更多业务

'com.businesshall.activity.SafeNumActivity' 安心小号
'com.zjmobile.app.Chongzhibao' 应用宝
'addr=com.businesshall.activity.MyBusinessActivity&type=typevalue1'已购订业务查询value 
'addr=com.businesshall.activity.LocationActivity&type=typevalue1'附近营业厅
'addr=com.businesshall.activity.LocationActivity&type=typevalue2'宽带覆盖
'addr=com.businesshall.activity.OrderActivity&type=marketidvalue2010020140313002'具体业务
'addr=com.businesshall.activity.MessageActivity&type=MESSAGE_TYPEvalue0'我的消息

 'addr=xuniwang'虚拟网
 'addr=4gzixuan'4g自选

安卓针对2.1.4 流量加油包特有： 
'addr=com.chinamobile.flow.activity.FlowOrderActivity&type=typevalue1'  type=1:加油包
'addr=com.chinamobile.flow.activity.FlowOrderActivity&type=typevalue2'  type=2:夜间流量
'addr=com.chinamobile.flow.activity.FlowOrderActivity&type=typevalue3'  type=3:其他流量

        </pre>

### ios

<pre class="prettyprint linenums prettyprinted">(带zjmobilesjyyt前缀用于外部唤醒 外部唤醒时才涉及到_separator_分隔符问题，内部跳转是用&符号连接。)
外部唤醒：
一级页面：
'zjmobilesjyyt://RootViewController'首页
'zjmobilesjyyt://QueryViewController'业务查询
'zjmobilesjyyt://ManageViewController'业务办理
'zjmobilesjyyt://DiscountViewController'优惠活动

(ios：_separator_ 分隔符 版本限制为：>=2.3.2 低于此版本应该用&分隔符，外部H5无法判断版本号，此处遗留bug)

二三级页面：
'zjmobilesjyyt://Main_separator_SettingViewController'设置
'zjmobilesjyyt://Main_separator_FeedbackViewController'意见反馈
'zjmobilesjyyt://Main_separator_BillViewController'账单查询
'zjmobilesjyyt://Main_separator_PackageViewController'套餐余量
'zjmobilesjyyt://Main_separator_OrderedViewController'已订业务
'zjmobilesjyyt://Main_separator_FNRootViewController'家庭亲情网
'zjmobilesjyyt://Main_separator_PointsQueryViewController'我的积分（积分兑换）
'zjmobilesjyyt://Main_separator_RechargeViewController'话费充值
'zjmobilesjyyt://Main_separator_RechargeRecordViewController'充值记录
'zjmobilesjyyt://Main_separator_PackageChangeViewController'套餐变更 （换套餐 已下线）
'zjmobilesjyyt://Main_separator_MorePackageViewController'更多业务
'zjmobilesjyyt://Main_separator_HotBusinessViewController'热门业务
'zjmobilesjyyt://Main_separator_AboutMeViewController'关于
'zjmobilesjyyt://Main_separator_FAQViewController'常见问题
'zjmobilesjyyt://Main_separator_PasswordModificationViewController'密码修改
'zjmobilesjyyt://Main_separator_PointsExchangeRecordViewController'积分兑换记录

Flow—流量专区故事板
'zjmobilesjyyt://Flow_separator_FlowMainController'流量专区
'zjmobilesjyyt://Flow_separator_FlowDayStatsController'每日流量消耗统计
'zjmobilesjyyt://Flow_separator_OtherFlowController'其他网上流量
'zjmobilesjyyt://Flow_separator_FlowSuitChangeController'流量订购
'zjmobilesjyyt://Flow_separator_FlowMonStatsController'历史流量使用查询

SecureNum—安心小号
'zjmobilesjyyt://SecureNum_separator_SecureNumTabBarViewController'安心小号首页

内部跳转：
一级页面：
'RootViewController'首页
'QueryViewController'业务查询
'ManageViewController'业务办理
'DiscountViewController'优惠活动

二三级页面：
'Main&SettingViewController'设置
'Main&FeedbackViewController'意见反馈
'Main&BillViewController'账单查询
'Main&PackageViewController'套餐余量
'Main&OrderedViewController'已订业务
'Main&FNRootViewController'家庭亲情网
'Main&PointsQueryViewController'我的积分 （积分兑换）
'Main&RechargeViewController'话费充值
'Main&RechargeRecordViewController'充值记录
'Main&PackageChangeViewController'套餐变更
'Main&MorePackageViewController'更多业务
'Main&HotBusinessViewController'热门业务
'Main&AboutMeViewController'关于
'Main&FAQViewController'常见问题
'Main&PasswordModificationViewController'密码修改
'Main&PointsExchangeRecordViewController'积分兑换记录

Flow—流量专区故事板
'Flow&FlowMainController'流量专区
'Flow&FlowDayStatsController'每日流量消耗统计
'Flow&OtherFlowController'其他网上流量
'Flow&FlowSuitChangeController'流量订购
'Flow&FlowMonStatsController'历史流量使用查询

附近营业厅：
'Map&NearBussinessHallVC'

SecureNum—安心小号
'SecureNum&SecureNumTabBarViewController'安心小号首页
应用宝：
'chongzhibao'
        </pre>

</section>

<section id="chama">

<div class="page-header">

# 插码规范

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">在每个工程文件夹中的js文件夹中引入3个插码文件：webtrends.hm.js webtrends.load.js webtrends.min.js
在开发文件中每个页面中引入 js/webtrends.load.js即可。
    </pre>

### 说明：参考demo

### demo：

[充值99折](http://app.m.zj.chinamobile.com/zjweb/sjyyt/chongzhiV2/index.html)![](images/demo13.jpg)</section>

<section id="qianduan">

<div class="page-header">

# 字体规范

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">1.1  字体(font-family)
设置字体：Helvetica,Arial ,sans-serif
引入公共css：base2016.css
1.2  字体大小(font-size)
统一rem为单位，用js控制根元素的字体大小，代码如下
前端引入adapt.js
并设置：
adapt(w);// w值为设计稿的1/2
    </pre>

### 说明：参考demo

### demo：

[前端空白模版](http://www.hssmwd.com/uploads/sjyyt/example/demo.html)![](images/demo14.jpg)</section>

<section id="marketid">

<div class="page-header">

# marketid

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">MARKETID  MARKETNAME
8010020140101010  金华购智能机送话费活动
2010020140101003  139邮箱
2010020140101004  手机炒股
2010020140101005  手机视频
8010020140101001  杭州动感地带优惠期长话包（新）
8010020140101006  iPhone 5s预订
8010020140101008  杭州购4G手机，赠4G‘和’包活动
8010020140101007  杭州购TD智能机送话费活动
8010020140101002  两城一家省内版
8010020140101003  两城一家省际版
8010020140101004  非常假期省内版
5010020140310001  4G飞享（自选）套餐
2010020140101006  来电管家
8010020140101005  非常假期省际版
2010020140101002  无线音乐俱乐部
6010020140101004  4G套餐内流量包
6010020140101006  4G移动数据流量包
6010020140101003  普通流量加油包
6010020140101005  4G流量加油包
2010020140101001  和阅读
6010020140101001  移动数据流量包
8010020141124001  流量加油包
6010020140101002  随意玩流量包
8010020140101009  家庭亲情网
2010020140312001  来电显示
2010020140312002  彩铃业务
2010020140312003  来电提醒
6010020140527003  4G套餐内流量包
2010020140312004  天气预报
2010020140312005  漫游通
2010020140313001  夜话畅聊
2010020140313002  手机签名
2010020140313003  主叫彩铃
2010020140313004  全国漫游畅听包
2010020140313005  校园市话畅聊
5010020140310002  全球通上网套餐（2012版）
5010020140310003  全球通商旅套餐（2012版）
8010020140101011  虚拟网
8010020140101012  积分兑换话费
2010020140313006  和通讯录
2010020140313007  短信业务（神州行）
2010020140313008  短信业务（全球通）
2010020140313009  短信业务（动感地带）
2010020140313010  杭州校园动感3元长话包
6010020140527004  4G移动数据流量包
6010020140527001  移动数据流量包
2010020160407001  短信包 
2010020160226001  4G高清通话 
2010020151221001  和视界 
2010020160113001  移送省钱快报 
2010020140313006  和通讯录 
2010020150624001  WLAN流量计费产品 
    </pre>

</section>

<section id="anquanjiagu">

<div class="page-header">

# H5安全加固

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">请查看 http://www.nczzt.com/uploads/anquanjiagu/js/zjreload.js
    </pre>

### 说明：参考demo

### demo：

[H5安全加固](http://www.nczzt.com/uploads/anquanjiagu/index.html)![](images/demo14.jpg)</section>

<section id="closeback">

<div class="page-header">

# H5能力之关闭和后退

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">引入zjcloseback.js
ZJ.doClose();
ZJ.doReturn();
具体请查看 http://www.nczzt.com/uploads/closeback/js/zjcloseback.js 
最新能力要求安卓 ios 版本 : >3.0.2
    </pre>

### 说明：参考demo

### demo：

[H5能力之关闭和后退](http://www.nczzt.com/uploads/closeback/index.html)![](images/demo21.jpg)</section>

<section id="qrcode">

<div class="page-header">

# H5能力之调用手厅扫一扫

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">引入zjqrcode.js
ZJ.Qrcode.doQrcode();

具体请查看 http://www.nczzt.com/uploads/qrcode/js/zjqrcode.js
最新能力要求版本: ios >3.0.2 ; 安卓 >= 3.1.1

此扫一扫是获取二维码中的字符串 回调给前端页面使用
    </pre>

### 说明：参考demo

### demo：

[H5能力之调用手厅扫一扫](http://www.nczzt.com/uploads/qrcode/index.html)![](images/demo21.jpg)</section>

<section id="nettype">

<div class="page-header">

# H5能力之手机网络类型检测

</div>

### 参数说明

<pre class="prettyprint linenums prettyprinted">zjnettype.js
ZJ.Nettype.getNetType();

具体请查看 http://www.nczzt.com/uploads/js/zjnettype.js
最新能力要求版本: ios >3.0.2 ; 安卓 > 3.1.1

获取当前手机的网络类型，字符串类型回调给前端页面使用：2G 3G 4G WIFI 获取不到时返回：NONE

获取方式方法类似版本号，ios如有bug 可加点击获取或者延时处理，参考获取版本号的方法
    </pre>

### 说明：参考demo

### demo：

[H5能力之手机网络类型检测](http://www.nczzt.com/uploads/nettype.html)![](images/demo23.jpg)</section>

</div>

</div>

</div>