<!DOCTYPE html>
<html lang='zh-CN'>
<head>
<title>doc/XXL-JOB官方文档.md · 许雪里/xxl-job - Gitee.com</title>
<meta content='on' http-equiv='x-dns-prefetch-control'>
<link href='//e.gitee.com' rel='dns-prefetch'>
<link href='//files.gitee.com' rel='dns-prefetch'>
<link href='//toscode.gitee.com' rel='dns-prefetch'>
<link href='https://cn-assets.gitee.com' rel='dns-prefetch'>
<link href='https://portrait.gitee.com' rel='dns-prefetch'>
<link rel="shortcut icon" type="image/vnd.microsoft.icon" href="https://cn-assets.gitee.com/assets/favicon-9007bd527d8a7851c8330e783151df58.ico" />
<link rel="canonical" href="https://gitee.com/xuxueli0323/xxl-job" />
<meta content='gitee.com/xuxueli0323/xxl-job git https://gitee.com/xuxueli0323/xxl-job.git' name='go-import'>
<meta charset='utf-8'>
<meta content='always' name='referrer'>
<meta content='Gitee' property='og:site_name'>
<meta content='Object' property='og:type'>
<meta content='https://gitee.com/xuxueli0323/xxl-job/blob/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md' property='og:url'>
<meta content='https://gitee.com/static/images/logo_themecolor.png' itemprop='image' property='og:image'>
<meta content='doc/XXL-JOB官方文档.md · 许雪里/xxl-job - Gitee.com' itemprop='name' property='og:title'>
<meta content='一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。' property='og:description'>
<meta content='码云,Gitee,代码托管,Git,Git@OSC,Gitee.com,开源,内源,项目管理,版本控制,开源代码,代码分享,项目协作,开源项目托管,免费代码托管,Git代码托管,Git托管服务' name='Keywords'>
<meta content='一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。' itemprop='description' name='Description'>
<meta content='pc,mobile' name='applicable-device'>

<meta content="IE=edge" http-equiv="X-UA-Compatible" />
<meta name="csrf-param" content="authenticity_token" />
<meta name="csrf-token" content="k2zSjdFNymaOOIyQPc8G/J9iA9Iw+aizVyph44rmbfUvXbdCgb2PGk5YlGzWGibpmyJLvGVISPv+Yx/wDTjUbw==" />

<link rel="stylesheet" media="all" href="https://cn-assets.gitee.com/assets/application-be2c923ad69d128fdecca4706934a58e.css" />
<script>
//<![CDATA[
window.gon = {};gon.locale="zh-CN";gon.sentry_dsn=null;gon.baidu_register_hm_push=null;gon.sensor={"server_url":"https://haveaniceday.gitee.com:3443/sa?project=production","sdk_url":"https://cn-assets.gitee.com/assets/static/sensors-sdk-2f850fa5b654ad55ac0993fda2f37ba5.js","page_type":"其他"};gon.info={"controller_path":"blob","action_name":"show","current_user":false};gon.tour_env={"current_user":null,"action_name":"show","original_url":"https://gitee.com/xuxueli0323/xxl-job/blob/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md","controller_path":"blob"};gon.http_clone="https://gitee.com/xuxueli0323/xxl-job.git";gon.user_project="xuxueli0323/xxl-job";gon.manage_branch="管理分支";gon.manage_tag="管理标签";gon.enterprise_id=0;gon.create_reaction_path="/xuxueli0323/xxl-job/reactions";gon.ipipe_base_url="https://go-api.gitee.com";gon.artifact_base_url="https://go-repo.gitee.com";gon.gitee_go_remote_url="https://go.gitee.com/assets";gon.gitee_go_active=false;gon.current_project_is_mirror=false;gon.show_repo_comment=false;gon.diagram_viewer_path="https://diagram-viewer.giteeusercontent.com";gon.ref="master";
//]]>
</script>
<script src="https://cn-assets.gitee.com/assets/static/sensor-6269b9ad61bbcdaff20078e5dcff62d5.js"></script>
<script src="https://cn-assets.gitee.com/assets/static/sentry-5.1.0-a823fb0be1b61c5d7ca4a89f0536cb0a.js"></script>
<script src="https://cn-assets.gitee.com/assets/application-bd2a74541a7204a682192967e5592250.js"></script>
<script src="https://cn-assets.gitee.com/assets/lib/jquery.timeago.zh-CN-4a4818e98c1978d2419ab19fabcba740.js"></script>

<link rel="stylesheet" media="all" href="https://cn-assets.gitee.com/assets/projects/application-46b94c31ba11ae8c37eacce2bdb5603e.css" />
<script src="https://cn-assets.gitee.com/assets/projects/app-2b3d989fcf407be52d8dfd35c2298749.js"></script>

<script src="//res.wx.qq.com/open/js/jweixin-1.2.0.js"></script>
<script>
  var title = document.title.replace(/( - Gitee| - 码云)$/, '')
      imgUrl = '';
  
  document.addEventListener('DOMContentLoaded', function(event) {
    var imgUrlEl = document.querySelector('.readme-box .markdown-body > img, .readme-box .markdown-body :not(a) > img');
    imgUrl = imgUrlEl && imgUrlEl.getAttribute('src');
  
    if (!imgUrl) {
      imgUrlEl = document.querySelector('meta[itemprop=image]');
      imgUrl = imgUrlEl && imgUrlEl.getAttribute('content');
      imgUrl = imgUrl || "https://gitee.com/static/images/logo_themecolor.png";
    }
  
    wx.config({
      debug: false,
      appId: "wxff219d611a159737",
      timestamp: "1675329814",
      nonceStr: "db6aa2cd9de614d569d05582dcfe7c7e",
      signature: "445f829170c6ee93eee8691444b6fe1f424381d0",
      jsApiList: [
        'onMenuShareTimeline',
        'onMenuShareAppMessage'
      ]
    });
  
    wx.ready(function () {
      wx.onMenuShareTimeline({
        title: title, // 分享标题
        link: "https://gitee.com/xuxueli0323/xxl-job/blob/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md", // 分享链接，该链接域名或路径必须与当前页面对应的公众号JS安全域名一致
        imgUrl: imgUrl // 分享图标
      });
      wx.onMenuShareAppMessage({
        title: title, // 分享标题
        link: "https://gitee.com/xuxueli0323/xxl-job/blob/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md", // 分享链接，该链接域名或路径必须与当前页面对应的公众号JS安全域名一致
        desc: document.querySelector('meta[name=Description]').getAttribute('content'),
        imgUrl: imgUrl // 分享图标
      });
    });
    wx.error(function(res){
      console.error('err', res)
    });
  })
</script>

<script type='text/x-mathjax-config'>
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    displayMath: [["$$","$$"],["\\[","\\]"]],
    processEscapes: true,
    skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code'],
    ignoreClass: "container|files",
    processClass: "markdown-body"
  }
});
</script>
<script src="https://cn-assets.gitee.com/uploads/resources/MathJax-2.7.2/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

<script>
  (function () {
    var messages = {
      'zh-CN': {
        addResult: '增加 <b>{term}</b>',
        count: '已选择 {count}',
        maxSelections: '最多 {maxCount} 个选择',
        noResults: '未找到结果',
        serverError: '连接服务器时发生错误'
      },
      'zh-TW': {
        addResult: '增加 <b>{term}</b>',
        count: '已選擇 {count}',
        maxSelections: '最多 {maxCount} 個選擇',
        noResults: '未找到結果',
        serverError: '連接服務器時發生錯誤'
      }
    }
  
    if (messages[gon.locale]) {
      $.fn.dropdown.settings.message = messages[gon.locale]
    }
  }());
</script>

<script>
  var userAgent = navigator.userAgent;
  var isLessIE11 = userAgent.indexOf('compatible') > -1 && userAgent.indexOf('MSIE') > -1;
  if(isLessIE11){
    var can_access = ""
    if (can_access != "true"){
      window.location.href = "/incompatible.html";
    }
  }
  document.addEventListener("error", function (ev) {
    var elem = ev.target;
    if (elem.tagName.toLowerCase() === 'img') {
      elem.src = "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAAAAACIM/FCAAACh0lEQVR4Ae3ch5W0OgyG4dt/mQJ2xgQPzJoM1m3AbALrxzrf28FzsoP0HykJEEAAAUQTBBBAAAEEEEAAAQQQQAABBBBAAAEEEEAAAQQQQAABBBBAAAEEkKK0789+GK/I2ezfQB522PnS1qc8pGgXvr4tE4aY0XOUWlGImThWgyCk6DleixzE7qwBkg/MGiDPlVVAyp1VQGrPKiACDhFI6VkF5LmzCki+sg7IwDoglnVAil0IMkeG9CyUiwsxLFUVFzJJOQaKCjFCDN9RXMjIX7W6ztZXZDKKCyn8sWJvH+nca7WHDN9lROlAliPH9iRKCPI4cswFJQWxB46toLQgQ9jhn5QYZA9DOkoMUoQde5YapAxDWkoNYsOQR3KQd9CxUnIQF4S49CB9ENKlBxmDEKsFUgMCCCCAAHIrSF61f6153Ajy8nyiPr8L5MXnmm4CyT2fzN4DUvHZ+ntA2tOQBRBAAAEEEEAAAQQQ7ZBaC6TwSiDUaYHQ2yuB0MN+ft+43whyrs4rgVCjBUKTFshLC6TUAjGA3AxSaYFYLZBOC2RUAsk8h5qTg9QcbEoOsoQhQ2qQhsO5xCD5dgB5JQaZ+KBKGtKecvR81Ic0ZDjByKdDx0rSEDZ/djQbH+bkIdvfJFm98BfV8hD2zprfVdlu9PxVeyYAkciREohRAplJCaRSAplJCcQogTjSAdlyHRBvSAekJR0QRzogA+mADJkOiCPSAPEtqYBshlRAXC43hxix2QiOuEZkVERykGyNo9idIZKE0HO7XrG6OiMShlDWjstVzdPgXtUH9v0CEidAAAEEEEAAAQQQQAABBBBAAAEEEEAAAQQQQAABBBBAAAEEEEAAAQQQQP4HgjZxTpdEii0AAAAASUVORK5CYII=";
    }
  }, true);
</script>
</head>

<body class='git-project lang-zh-CN'>
<header class='common-header fixed noborder' id='git-header-nav'>
<div class='ui container'>
<div class='ui menu header-menu header-container'>
<div class='git-nav-expand-bar'>
<i class='iconfont icon-mode-table'></i>
</div>
<div class='gitee-nav__sidebar'>
<div class='gitee-nav__sidebar-container'>
<div class='gitee-nav__sidebar-top'>
<div class='gitee-nav__avatar-box'></div>
<div class='gitee-nav__buttons-box'>
<a class="ui button small fluid orange" href="/login">登录</a>
<a class="ui button small fluid basic is-register" href="/signup">注册</a>
</div>
</div>
<div class='gitee-nav__sidebar-middle'>
<div class='gitee-nav__sidebar-list'>
<ul>
<li class='gitee-nav__sidebar-item'>
<a href="/explore"><i class='iconfont icon-ic-discover'></i>
<span class='gitee-nav__sidebar-name'>开源软件</span>
</a></li>
<li class='gitee-nav__sidebar-item'>
<a href="/enterprises"><i class='iconfont icon-ic-enterprise'></i>
<span class='gitee-nav__sidebar-name'>企业版</span>
</a></li>
<li class='gitee-nav__sidebar-item'>
<a href="/education"><i class='iconfont icon-ic-education'></i>
<span class='gitee-nav__sidebar-name'>高校版</span>
</a></li>
<li class='gitee-nav__sidebar-item split-line'></li>
<li class='gitee-nav__sidebar-item'>
<a href="/search"><i class='iconfont icon-ic-search'></i>
<span class='gitee-nav__sidebar-name'>搜索</span>
</a></li>
<li class='gitee-nav__sidebar-item'>
<a href="/help"><i class='iconfont icon-help-circle'></i>
<span class='gitee-nav__sidebar-name'>帮助中心</span>
</a></li>
<li class='gitee-nav__sidebar-item'>
<a href="/terms"><i class='iconfont icon-file'></i>
<span class='gitee-nav__sidebar-name'>使用条款</span>
</a></li>
<li class='gitee-nav__sidebar-item'>
<a href="/about_us"><i class='iconfont icon-issuepx'></i>
<span class='gitee-nav__sidebar-name'>关于我们</span>
</a></li>
</ul>
</div>
</div>
<div class='gitee-nav__sidebar-bottom'>
<div class='gitee-nav__sidebar-close-button'>
<i class='fa fa-angle-double-left'></i>
</div>
</div>
</div>
</div>

<div class='item gitosc-logo'>
<a href="https://gitee.com"><img alt='Gitee — 基于 Git 的代码托管和研发协作平台' class='ui inline image' height='28' src='/static/images/logo.svg?t=158106664' title='Gitee — 基于 Git 的代码托管和研发协作平台' width='95'>
<img alt='Gitee — 基于 Git 的代码托管和研发协作平台' class='ui inline black image' height='28' src='/static/images/logo-black.svg?t=158106664' title='Gitee — 基于 Git 的代码托管和研发协作平台' width='95'>
</a></div>
<a title="开源软件" class="item " href="/explore">开源软件
</a><a title="企业版" class="item " sa_evt="click_GiteeCommunity_tab_En" href="/enterprises">企业版
<sup class='ui red label'>
特惠
</sup>
</a><a title="高校版" class="item " href="/education">高校版
</a><a title="私有云" class="item" target="_blank" href="https://gitee.cn?utm_source=giteecom">私有云
</a><a title="博客" class="item" id="gitee-blog" target="_blank" href="https://blog.gitee.com/?utm_sources=site_nav">博客
</a><div class='center responsive-logo'>
<a href="https://gitee.com"><img alt='Gitee — 基于 Git 的代码托管和研发协作平台' class='ui inline image' height='24' src='/static/images/logo.svg?t=158106664' title='Gitee — 基于 Git 的代码托管和研发协作平台' width='85'>
<img alt='Gitee — 基于 Git 的代码托管和研发协作平台' class='ui inline black image' height='24' src='/static/images/logo-black.svg?t=158106664' title='Gitee — 基于 Git 的代码托管和研发协作平台' width='85'>
</a></div>
<div class='right menu userbar right-header' id='git-nav-user-bar'>
<form class="ui item" id="navbar-search-form" data-text-require="搜索关键字不能少于1个" data-text-filter="搜索格式不正确" action="/search" accept-charset="UTF-8" method="get"><input name="utf8" type="hidden" value="&#x2713;" />
<input type="hidden" name="type" id="navbar-search-type" />
<input type="hidden" name="fork_filter" id="fork_filter" value="on" />
<div class='ui search header-search'>
<input type="text" name="q" id="navbar-search-input" value="" class="prompt" placeholder="搜开源" />
</div>
</form>

<script>
  var can_search_in_repo = 1,
      repo = "VG1wWmVrMTZVVE5aVkdNeVRUSlpQV0UzTmpObWE3NjNm",
      reponame = "xuxueli0323/xxl-job";
  
  $(function() {
    var $search = $('#navbar-search-form .ui.search');
    $search.search({
      apiSettings: {
        url: '/search/relative_project?q={query}',
        onResponse: function (res) {
          if (res && res.status === 200 && res.data) {
            var query = htmlSafe($search.search('get value'));
  
            res.data.map(function (item) {
              item.path_ns = '/' + item.path_ns;
              item.icon = 'iconfont icon-project-public';
            });
            res.data.unshift({
              name_ns: "在全站搜索 <b class='hl'>" + query +"</b> 相关项目",
              path_ns: '/search?fork_filter=on&q=' + query,
              icon: 'iconfont icon-search'
            });
            return res;
          } else {
            return { data: [] };
          }
        }
      },
      fields: {
        results: 'data',
        description: 'name_ns',
        url: 'path_ns',
        icon: 'icon'
      },
      minCharacters: 1,
      maxResults: 10,
      searchDelay: 250,
      showNoResults: false,
      transition: 'fade'
    });
  });
</script>

<div class='ui item' id='feature-update-notice'>
<div class='notice-update-icon'>
<a class="notice-update-popup click-knowed" title="" href="javascript:void(0)"><img alt="功能更新" title="" class="bubl_icon bubl-off-icon" src="https://cn-assets.gitee.com/assets/bulb_off-24ee940be20998aace89a3f040cbc704.svg" />
<img alt="功能更新" title="" class="bubl_icon bubl-on-icon" src="https://cn-assets.gitee.com/assets/bulb_on-3986b1dc417285398e3d15671bd8f261.svg" />
</a></div>
<div class='feature-update-notice-panel menu'>
<div class='notice-img'>
<img alt="" title="" class="notice-img-show" src="" />
</div>
<div class='notice-update-title'></div>
<div class='notice-update-des'></div>
<div class='notice-btn-list d-flex-between'>
<button name="button" type="button" class="ui basic orange button btn-notice btn-knowed click-knowed" style="margin-right: 0">我知道了</button>
<a class="ui button orange btn-notice btn-details click-knowed" target="_blank" href="">查看详情</a>
</div>
</div>
</div>

<a class="item git-nav-user__login-item" sa_evt="login_show" sa_referrer_url="" sa_referrer_action="站导航右上角-登录按钮" sa_referrer_type="其他" href="/login">登录
</a><a class="item git-nav-user__register-item" sa_evt="register_show" sa_referrer_url="" sa_referrer_action="站导航右上角-注册按钮" sa_referrer_type="其他" href="/signup">注册
</a><script>
  $('.destroy-user-session').on('click', function() {
    $.cookie('access_token', null, { path: '/' });
  })
</script>

</div>
</div>
</div>
</header>
<script>
  Gitee.initNavbar()
  Gitee.initRepoRemoteWay()
  $.cookie('user_locale',null)
</script>

<script>
  var userAgent = navigator.userAgent;
  var isLessIE11 = userAgent.indexOf('compatible') > -1 && userAgent.indexOf('MSIE') > -1;
  if(isLessIE11){
    var can_access = ""
    if (can_access != "true"){
      window.location.href = "/incompatible.html";
    }
  }
</script>

<div class='fixed-notice-infos'>
<div class='all-messages'>
</div>
<div class='ui container'>
<div class='flash-messages' id='messages-container'></div>
</div>
<script>
  (function() {
    $(function() {
      var $error_box, alertTip, notify_content, notify_options, template;
      template = '<div data-notify="container" class="ui {0} message" role="alert">' + '<i data-notify="dismiss" class="close icon"></i>' + '<span data-notify="message">{2}</span>' + '</div>';
      notify_content = null;
      notify_options = {};
      alertTip = '';
      $error_box = $(".flash_error.flash_error_box");
      if (notify_options.type === 'error' && $error_box.length > 0 && !$.isEmptyObject(notify_content.message)) {
        if (notify_content.message === 'captcha_fail') {
          alertTip = "验证码不正确";
        } else if (notify_content.message === 'captcha_expired') {
          alertTip = "验证码已过期，请点击刷新";
        } else if (notify_content.message === 'not_found_in_database') {
          alertTip = "帐号或者密码错误";
        } else if (notify_content.message === 'not_found_and_show_captcha') {
          alertTip = "帐号或者密码错误";
        } else if (notify_content.message === 'phone_captcha_fail') {
          alertTip = "手机验证码不通过";
        } else {
          alertTip = notify_content.message;
        }
        return $error_box.html(alertTip).show();
      } else if (notify_content) {
        if ("show" === 'third_party_binding') {
          return $('#third_party_binding-message').html(notify_content.message).addClass('ui message red');
        }
        notify_options.delay = 3000;
        notify_options.template = template;
        notify_options.offset = {
          x: 10,
          y: 30
        };
        notify_options.element = '#messages-container';
        return $.notify(notify_content, notify_options);
      }
    });
  
  }).call(this);
</script>

</div>
<script>
  (function() {
    $(function() {
      var setCookie;
      setCookie = function(name, value) {
        $.cookie(name, value, {
          path: '/',
          expires: 365
        });
      };
      $('#remove-bulletin, #remove-bulletin-dashboard').on('click', function() {
        setCookie('remove_bulletin', "gitee-maintain-1671157534");
        $('#git-bulletin').hide();
      });
      $('#remove-member-bulletin').on('click', function() {
        setCookie('remove_member_bulletin', "gitee_member_bulletin");
        $(this).parent().hide();
      });
      return $('#remove-gift-bulletin').on('click', function() {
        setCookie('remove_gift_bulletin', "gitee-gift-bulletin");
        $(this).parent().hide();
      });
    });
  
  }).call(this);
</script>
<script>
  function closeMessageBanner(pthis, type, val) {
    var json = {}
  
    val = typeof val === 'undefined' ? null : val
    $(pthis).parent().remove()
    if (type === 'out_of_enterprise_member') {
      json = {type: type, data: val}
    } else if (type === 'enterprise_overdue') {
      json = {type: type, data: val}
    }
    $.post('/profile/close_flash_tip', json)
  }
</script>

<div class='site-content'>
<div class='git-project-header'>
<div class='fixed-notice-infos'>
<div class='ui info icon floating message green' id='fetch-ok' style='display: none'>
<div class='content'>
<div class='header status-title'>
<i class='info icon status-icon'></i>
代码拉取完成，页面将自动刷新
</div>
</div>
</div>
<div class='ui info icon floating message error' id='fetch-error' style='display: none'>
<div class='content'>
<div class='header status-title'>
<i class='info icon status-icon'></i>
<span class='error_msg'></span>
</div>
</div>
</div>
</div>
<div class='ui container'>
<div class='git-project-categories'>
<a href="/explore">开源项目</a>
<span class='symbol'>></span>
<a href="/explore/program-develop">程序开发</a>
<span class='symbol'>&gt;</span>
<a href="/explore/task-schedule">作业/任务调度</a>
<span class='symbol and-symbol'>&&</span>
</div>

<div class='git-project-header-details'>
<div class='git-project-header-container'>
<div class='git-project-header-actions'>
<div class='ui tiny modal project-donate-modal' id='project-donate-modal'>
<i class='iconfont icon-close close'></i>
<div class='header'>捐赠</div>
<div class='content'>
捐赠前请先登录
</div>
<div class='actions'>
<a class='ui blank button cancel'>取消</a>
<a class='ui orange ok button' href='/login'>前往登录</a>
</div>
</div>
<div class='ui small modal wepay-qrcode'>
<i class='iconfont icon-close close'></i>
<div class='header'>
扫描微信二维码支付
<span class='wepay-cash'></span>
</div>
<div class='content weqcode-center'>
<img id='wepay-qrcode' src=''>
</div>
<div class='actions'>
<div class='ui cancel blank button'>取消</div>
<div class='ui ok orange button'>支付完成</div>
</div>
</div>
<div class='ui mini modal' id='confirm-alipay-modal'>
<div class='header'>支付提示</div>
<div class='content'>
将跳转至支付宝完成支付
</div>
<div class='actions'>
<div class='ui approve orange button'>确定</div>
<div class='ui blank cancel button'>取消</div>
</div>
</div>

<span class='ui buttons basic watch-container'>
<div class='ui dropdown button js-project-watch' data-watch-type='unwatch'>
<input type='hidden' value=''>
<i class='iconfont icon-watch'></i>
<div class='text'>
Watch
</div>
<i class='dropdown icon'></i>
<div class='menu'>
<a data-value="unwatch" class="item" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Watch" sa_referrer_type="其他" rel="nofollow" data-method="post" href="/xuxueli0323/xxl-job/unwatch"><i class='iconfont icon-msg-read'></i>
不关注
</a><a data-value="watching" class="item" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Watch" sa_referrer_type="其他" rel="nofollow" data-method="post" href="/xuxueli0323/xxl-job/watch"><i class='iconfont icon-msg-read'></i>
关注所有动态
</a><a data-value="releases_only" class="disabled item" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Watch" sa_referrer_type="其他" rel="nofollow" data-method="post" href="/xuxueli0323/xxl-job/release_only_watch"><i class='iconfont icon-msg-read'></i>
仅关注版本发行动态
</a><a data-value="ignoring" class="item" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Watch" sa_referrer_type="其他" rel="nofollow" data-method="post" href="/xuxueli0323/xxl-job/ignoring_watch"><i class='iconfont icon-msg-read'></i>
关注但不提醒动态
</a></div>
</div>
<style>
  .js-project-watch .text .iconfont {
    display: none; }
  .js-project-watch a, .js-project-watch a:hover {
    color: #000; }
  .js-project-watch .item > .iconfont {
    visibility: hidden;
    margin-left: -10px; }
  .js-project-watch .selected .iconfont {
    visibility: visible; }
  .js-project-watch .menu {
    margin-top: 4px !important; }
</style>
<script>
  $('.js-project-watch').dropdown({
    action: 'select',
    onChange: function(value, text, $selectedItem) {
      var type = value === 'unwatch' ? 'Watch' : 'Watching';
      $(this).children('.text').text(type);
      $(this).dropdown('set selected', value)
    }
  });
</script>

<a class="ui button action-social-count" title="1832" href="/xuxueli0323/xxl-job/watchers">1.8K
</a></span>
<span class='basic buttons star-container ui'>
<a class="ui button star" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Star" sa_referrer_type="其他" href="/login"><i class='iconfont icon-star'></i>
Star
</a><a class="ui button action-social-count " title="10089" href="/xuxueli0323/xxl-job/stargazers">10.1K
</a></span>
<span class='ui basic buttons fork-container' title='无权 Fork 此仓库'>
<a class="ui button fork" title="你必须登录后才可以fork一个仓库" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="Fork" sa_referrer_type="其他" href="/login"><i class='iconfont icon-fork'></i>
Fork
</a><a class="ui button action-social-count disabled-style" title="5079" href="/xuxueli0323/xxl-job/members">5.1K
</a></span>
</div>
<h2 class='git-project-title mt-0 mb-0'>
<a title="GVP - Gitee 最有价值开源项目" class="ui small label git-project-gvp-badge" target="_blank" href="/gvp">GVP</a><a title="许雪里" class="author" href="/xuxueli0323">许雪里</a> / <a title="xxl-job" class="repository" target="" style="padding-bottom: 0px; margin-right: 4px" sa_evt="repoClick" sa_location="其他" sa_url="" sa_repo_id="663347" href="/xuxueli0323/xxl-job">xxl-job</a>
<input type="hidden" name="recomm_at" id="recomm_at" value="2015-12-06 18:57" />
<input type="hidden" name="project_title" id="project_title" value="许雪里/xxl-job" />
</h2>
</div>
</div>
</div>
<script>
  var title_import_url = "https://github.com/xuxueli/xxl-job.git";
  var title_post_url = "/xuxueli0323/xxl-job/update_import";
  var title_fork_url = "/xuxueli0323/xxl-job/sync_fork";
  var title_project_path = "xxl-job";
  var title_p_name = "xxl-job";
  var title_p_id= "663347";
  var title_description = "一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。";
  var title_form_authenticity_token = "U+Y7LVKcVh1ii88K8Y7V4qDf/7RIsqt+MBV9dcKXavfv117iAmwTYaLr1/YaW/X3pJ+32h0DSzaZXANmRUnTbQ==";
  var watch_type = "unwatch";
  var checkFirst = false;
  
  $('.js-project-watch').dropdown('set selected', watch_type);
  $('.checkbox.sync-wiki').checkbox();
  $('.checkbox.team-member-checkbox').checkbox();
</script>
<style>
  i.loading, .icon-sync.loading {
    -webkit-animation: icon-loading 1.2s linear infinite;
    animation: icon-loading 1.2s linear infinite;
  }
  .qrcode_cs {
    float: left;
  }
  .check-sync-wiki {
    float: left;
    height: 28px;
    line-height: 28px;
  }
  .sync-wiki-warn {
    color: #e28560;
  }
</style>

<div class='git-project-nav'>
<div class='ui container'>
<div class='ui secondary pointing menu'>
<a class="item active" href="/xuxueli0323/xxl-job"><i class='iconfont icon-code'></i>
代码
</a><a class="item " href="/xuxueli0323/xxl-job/issues"><i class='iconfont icon-task'></i>
Issues
<span class='ui mini circular label'>
152
</span>
</a><a class="item " href="/xuxueli0323/xxl-job/pulls"><i class='iconfont icon-pull-request'></i>
Pull Requests
<span class='ui mini circular label'>
13
</span>
</a><a class="item " href="/xuxueli0323/xxl-job/wikis"><i class='iconfont icon-wiki'></i>
Wiki
</a><a class="item  " href="/xuxueli0323/xxl-job/graph/master"><i class='iconfont icon-statistics'></i>
统计
</a><a class="item " href="/xuxueli0323/xxl-job/gitee_go"><i class='iconfont icon-workflow'></i>
流水线
</a><div class='item'>
<div class='ui pointing top right dropdown git-project-service'>
<div>
<i class='iconfont icon-service'></i>
服务
<i class='dropdown icon'></i>
</div>
<div class='menu' style='display:none'>
<a class="item" href="/xuxueli0323/xxl-job/pages"><img src="/static/images/logo-en.svg" alt="Logo en" />
<div class='item-title'>
Gitee Pages
</div>
</a><a class="item" href="/xuxueli0323/xxl-job/javadoc"><img src="https://cn-assets.gitee.com/assets/maven-bd58aee84f266d64d4b8ce5b006a9fcf.png" alt="Maven" />
<div class='item-title'>
JavaDoc
</div>
</a><a class="item" href="/xuxueli0323/xxl-job/quality_analyses?platform=sonar_qube"><img src="https://cn-assets.gitee.com/assets/sonar_mini-5e1b54bb9f6c951d97fb778ef623afea.png" alt="Sonar mini" />
<div class='item-title'>
质量分析
</div>
</a><a class="item" target="_blank" href="https://gitee.com/help/articles/4193"><img src="https://cn-assets.gitee.com/assets/jenkins_for_gitee-554ec65c490d0f1f18de632c48acc4e7.png" alt="Jenkins for gitee" />
<div class='item-title'>
Jenkins for Gitee
</div>
</a><a class="item" target="_blank" href="https://gitee.com/help/articles/4285"><img src="https://cn-assets.gitee.com/assets/baidu_efficiency_cloud-81a98c2eb67fac83b1453ca3d2feb326.svg" alt="Baidu efficiency cloud" />
<div class='item-title'>
百度效率云
</div>
</a><a class="item" target="_blank" href="https://gitee.com/help/articles/4318"><img src="https://cn-assets.gitee.com/assets/cloudbase-1197b95ea3398aff1df7fe17c65a6d42.png?20200925" alt="Cloudbase" />
<div class='item-title'>
腾讯云托管
</div>
</a><a class="item" target="_blank" href="https://gitee.com/help/articles/4330"><img src="https://cn-assets.gitee.com/assets/cloud_serverless-686cf926ced5d6d2f1d6e606d270b81e.png" alt="Cloud serverless" />
<div class='item-title'>
腾讯云 Serverless
</div>
</a><a class="item" href="/xuxueli0323/xxl-job/open_sca"><img src="https://cn-assets.gitee.com/assets/open_sca/logo-9049ced662b2f9936b8001e6f9cc4952.png" alt="Logo" />
<div class='item-title'>
悬镜安全
</div>
</a><button class='ui orange basic button quit-button' id='quiting-button'>
我知道了，不再自动展开
</button>
</div>
</div>
</div>
</div>
</div>
</div>
<script>
  $('.git-project-nav .ui.dropdown').dropdown({ action: 'nothing' });
  var gitee_reward_config = JSON.parse(localStorage.getItem('gitee_reward_config') || null) || false
  var $settingText = $('.setting-text')
  // 如果没有访问过
  if(!gitee_reward_config) $settingText.addClass('red-dot')
</script>
<style>
  .git-project-nav i.checkmark.icon {
    color: green;
  }
  #quiting-button {
    display: none;
  }
  
  .git-project-nav .dropdown .menu.hidden:after {
    visibility: hidden !important;
  }
</style>
<script>
  isSignIn = false
  isClickGuide = false
  $('#git-versions.dropdown').dropdown();
  $.ajax({
    url:"/xuxueli0323/xxl-job/access/add_access_log",
    type:"GET"
  });
  $('#quiting-button').on('click',function() {
    $('.git-project-service').click();
    if (isSignIn) {
      $.post("/projects/set_service_guide")
    }
    $.cookie("Serve_State", true, { expires: 3650, path: '/'})
    $('#quiting-button').hide();
  });
  if (!(isClickGuide || $.cookie("Serve_State") == 'true')) {
    $('.git-project-service').click()
    $('#quiting-button').show()
  }
</script>

</div>
<div class='ui container'>
<div class='register-guide'>
<div class='register-container'>
<div class='regist'>
加入 Gitee
</div>
<div class='description'>
与超过 800 万 开发者一起发现、参与优秀开源项目，私有仓库也完全免费 ：）
</div>
<a class="ui orange button free-registion" sa_evt="register_show" sa_referrer_url="" sa_referrer_action="免费加入" sa_referrer_type="其他" href="/signup?from=project-guide">免费加入</a>
<div class='login'>
已有帐号？
<a href="/login?from=project-guide">立即登录</a>
</div>
</div>
</div>

<div class='git-project-content-wrapper'>

<div class='ui grid' id='project-wrapper'>
<div class='sixteen wide column'>
<div class='git-project-content' id='git-project-content'>
<div class='row'>
<div class='git-project-desc-wrapper'>
<script>
  $('.git-project-desc-wrapper .ui.dropdown').dropdown();
  if (false) {
    gon.project_new_blob_path = "/xuxueli0323/xxl-job/new/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md"
    bindShowModal({
      el: $('.no-license .project-license__create'),
      complete: function(data, modal) {
        if (!data.haveNoChoice && !data.data) {
          Flash.show('请选择一项开源许可证')
        } else {
          location.href = gon.project_new_blob_path + '?license=' + data.data
        }
      },
      skip: function () {
        location.href = gon.project_new_blob_path + '?license'
      }
    });
  }
  
  $(".project-admin-action-box .reject").click(function() {
    var reason = $('[name=review-reject-reason]').val();
    if (!reason) {
      Flash.error('请选择不通过理由')
      return
    }
    $.ajax({
      type: 'POST',
      url: "/admin/shumei_content/shumei_check/reject_project_public",
      data: {
        reason: reason,
        status: 'rejected',
        project_id: 663347
      },
      success: function(result){
        if(result.status == 'success'){
          window.location.reload();
        }else{
          Flash.error(result.message)
        }
      }
    })
  })
  
  $(".project-admin-action-box .approve").click(function(){
  
    $.ajax({
      type: 'POST',
      url: "/admin/shumei_content/shumei_check/reject_project_public",
      data: {
        status: 'approved',
        project_id: 663347
      },
      success: function(result){
        if(result.status == 'success'){
          window.location.reload();
        }else{
          Flash.error(result.message)
        }
      }
    })
  })
  
  $(".project-admin-action-box .waiting").click(function(){
  
    $.ajax({
      type: 'POST',
      url: "/admin/shumei_content/shumei_check/reject_project_public",
      data: {
        status: 'waiting',
        project_id: 663347
      },
      success: function(result){
        if(result.status == 'success'){
          window.location.reload();
        }else{
          Flash.error(result.message)
        }
      }
    })
  })
  
  $('i.help.circle.icon').popup({
    popup: '.no-license .ui.popup',
    position: 'right center'
  });
  
  $('#remove-no-license-message').on('click', function() {
    $.cookie("skip_repo_no_license_message_663347", 'hide', { expires: 365 });
    $('#user-no-license-message').hide();
    return;
  });
</script>
</div>

</div>
<div class='git-project-bread' id='git-project-bread'>
<div class='ui horizontal list mr-1'>
<div class='item git-project-branch-item'>
<input type="hidden" name="path" id="path" value="doc/XXL-JOB官方文档.md" />
<div class='ui top left pointing dropdown gradient button dropdown-has-tabs' id='git-project-branch'>
<input type="hidden" name="ref" id="ref" value="master" />
<div class='default text'>
master
</div>
<i class='dropdown icon'></i>
<div class='menu'>
<div class='ui left icon search input'>
<i class='iconfont icon-search'></i>
<input class='search-branch' placeholder='搜索分支' type='text'>
</div>
<div class='tab-menu'>
<div class='tab-menu-action' data-tab='branches'>
<a class="ui link button" href="/xuxueli0323/xxl-job/branches">管理</a>
</div>
<div class='tab-menu-action' data-tab='tags'>
<a class="ui link button" href="/xuxueli0323/xxl-job/tags">管理</a>
</div>
<div class='tab-menu-item' data-placeholder='搜索分支' data-tab='branches'>
分支 (14)
</div>
<div class='tab-menu-item' data-placeholder='搜索标签' data-tab='tags'>
标签 (31)
</div>
</div>
<div class='tab scrolling menu' data-tab='branches' id='branches_panel'>
<div data-value="master" class="item"><span>master</span></div>
<div data-value="2.3.1" class="item"><span>2.3.1</span></div>
<div data-value="2.3.0" class="item"><span>2.3.0</span></div>
<div data-value="2.2.0" class="item"><span>2.2.0</span></div>
<div data-value="2.1.2" class="item"><span>2.1.2</span></div>
<div data-value="2.0.2" class="item"><span>2.0.2</span></div>
<div data-value="v1.9.2" class="item"><span>v1.9.2</span></div>
<div data-value="v1.8" class="item"><span>v1.8</span></div>
<div data-value="v1.8.2" class="item"><span>v1.8.2</span></div>
<div data-value="v1.7" class="item"><span>v1.7</span></div>
<div data-value="v1.6" class="item"><span>v1.6</span></div>
<div data-value="v1.5" class="item"><span>v1.5</span></div>
<div data-value="v1.4" class="item"><span>v1.4</span></div>
<div data-value="v1.3" class="item"><span>v1.3</span></div>
</div>
<div class='tab scrolling menu' data-tab='tags'>
<div class='item' data-value='2.3.1'>2.3.1</div>
<div class='item' data-value='2.3.0'>2.3.0</div>
<div class='item' data-value='v2.2.0'>v2.2.0</div>
<div class='item' data-value='2.1.2'>2.1.2</div>
<div class='item' data-value='2.1.1'>2.1.1</div>
<div class='item' data-value='2.1.0'>2.1.0</div>
<div class='item' data-value='2.0.2'>2.0.2</div>
<div class='item' data-value='v2.0.1'>v2.0.1</div>
<div class='item' data-value='v2.0.0'>v2.0.0</div>
<div class='item' data-value='v1.9.2'>v1.9.2</div>
<div class='item' data-value='v1.9.1'>v1.9.1</div>
<div class='item' data-value='v1.9.0'>v1.9.0</div>
<div class='item' data-value='v1.8.2'>v1.8.2</div>
<div class='item' data-value='v1.8.1'>v1.8.1</div>
<div class='item' data-value='v1.8.0'>v1.8.0</div>
<div class='item' data-value='v1.7.2'>v1.7.2</div>
<div class='item' data-value='v1.7.1'>v1.7.1</div>
<div class='item' data-value='v1.7.0'>v1.7.0</div>
<div class='item' data-value='v1.6.2'>v1.6.2</div>
<div class='item' data-value='v1.6.1'>v1.6.1</div>
<div class='item' data-value='v1.6.0'>v1.6.0</div>
<div class='item' data-value='v1.5.2'>v1.5.2</div>
<div class='item' data-value='v1.5.1'>v1.5.1</div>
<div class='item' data-value='v1.5.0'>v1.5.0</div>
<div class='item' data-value='v1.4.2'>v1.4.2</div>
<div class='item' data-value='v1.4.0'>v1.4.0</div>
<div class='item' data-value='v1.3.2'>v1.3.2</div>
<div class='item' data-value='v1.3.1'>v1.3.1</div>
<div class='item' data-value='v1.3.0'>v1.3.0</div>
<div class='item' data-value='v1.2.0'>v1.2.0</div>
<div class='item' data-value='1.0.0.0'>1.0.0.0</div>
</div>
</div>
</div>
<style>
  .iconfont.icon-shieldlock {
    color: #8c92a4;
  }
</style>
<script>
  var $branchesDropdown = $('#branches_panel');
  var $searchNameInput = $('.search-branch');
  var concurrentRequestLock = false;
  var filterXSS = window.filterXSS;
  $branchesDropdown.scroll(function() {
    var branchesPanel = document.getElementById('branches_panel');
    var numOfBranches = $branchesDropdown.children().length;
    var pageToken = $branchesDropdown.children().last().text().trim();
    if (branchesPanel.clientHeight + branchesPanel.scrollTop + 37 > branchesPanel.scrollHeight && numOfBranches < 14) {
      loadData({ page_token: pageToken });
    }
  });
  
  $searchNameInput.on('input', window.globalUtils.debouce(function (e) {
    var $currentTab = $('.tab-menu-action.active');
    var numOfBranches = $branchesDropdown.children().length;
    if($currentTab.data('tab') === 'branches' && numOfBranches < 14) {
    var searchWord = $searchNameInput.val().trim();
      if (searchWord !== "") {
        loadData({ search: searchWord });
      } else {
        loadData({});
      }
    }
  }, 500));
  
  function loadData(data) {
    if (concurrentRequestLock) { return; }
      concurrentRequestLock = true;
      $.ajax({
        url: "/xuxueli0323/xxl-job/branches/load_more",
        type: 'GET',
        data: data,
        dataType: 'json',
        success: function (branches) {
          var html = '';
          var protectRule = '';
          if (data.search || !data.page_token) {
            $branchesDropdown.empty();
          }
          branches.forEach(function (branch) {
            var branchName = filterXSS(branch.name);
            if(branch.branch_type.value === 1) {
              var rule = filterXSS(branch.protection_rule.wildcard);
              protectRule = `<i
                 class="iconfont icon-shieldlock protected-branch-popup"
                 data-title="受保护分支"
                 data-content='保护规则： ${rule}'
                >
                </i>`
            }
            html += `<div data-value='${branchName}' class="item">
                      <span>${branchName}</span> ${protectRule}
                     </div>`
          });
          $branchesDropdown.append(html);
          $('.protected-branch-popup').popup()
        },
        complete: function () {
          concurrentRequestLock = false;
        }
    });
  }
</script>

<script>
  $(function () {
    Gitee.initTabsInDropdown($('#git-project-branch').dropdown({
      fullTextSearch: true,
      selectOnKeydown: true,
      action: function (text,value,el) {
        var oItemOrInitObject = el[0] || el
        var isNotSelect = oItemOrInitObject.dataset.tab && oItemOrInitObject.dataset.tab === 'branches'
        if(isNotSelect){
          console.warn("You didn't choose a branch")
          return
        } 
        var path = $('#path').val();
        var href = ['/xuxueli0323/xxl-job/tree', encodeURIComponent(value), path].join('/');
        window.location.href = href;
        return true
      },
      onNoResults: function (searchTerm) {
        //未找到结果
        return true
      },
    }));
    $('.protected-branch-popup').popup()
  })
</script>

</div>
</div>
<div class='git-project-right-actions pull-right'>
<div class='ui orange button' id='btn-dl-or-clone'>
克隆/下载
<i class='dropdown icon'></i>
</div>
<div class='git-project-download-panel for-project ui bottom right popup'>
<div class='ui small secondary pointing menu'>
<a class='item active' data-text='' data-type='http' data-url='https://gitee.com/xuxueli0323/xxl-job.git'>HTTPS</a>
<a class='item' data-text='' data-type='ssh' data-url='git@gitee.com:xuxueli0323/xxl-job.git'>SSH</a>
<a class='item' data-text="该仓库未启用SVN访问，请仓库管理员前往【&lt;a target='_blank' href=/xuxueli0323/xxl-job/settings&gt;仓库设置&lt;/a&gt;】开启。" data-type='svn' data-url=''>SVN</a>
<a class='item' data-text="该仓库未启用SVN访问，请仓库管理员前往【&lt;a target='_blank' href=/xuxueli0323/xxl-job/settings&gt;仓库设置&lt;/a&gt;】开启。" data-type='svn_ssh' data-url=''>SVN+SSH</a>
</div>
<div class='ui fluid right labeled small input download-url-panel'>
<input type="text" name="project_clone_url" id="project_clone_url" value="https://gitee.com/xuxueli0323/xxl-job.git" onclick="focus();select()" readonly="readonly" />
<div class='ui basic label'>
<div class='ui small basic orange button' data-clipboard-target='#project_clone_url' id='btn-copy-clone-url'>
复制
</div>
</div>
</div>
<div class='ui fluid right labeled warning-text forbid-warning-text'>

</div>
<hr>
<a class="ui fluid download link button" sa_evt="loginInform_show" sa_referrer_url="" sa_referrer_action="克隆/下载" sa_referrer_type="其他" href="javascript:void(0);"><i class='icon download'></i>
下载ZIP
</a><div class='download_repository_zip form modal tiny ui' id='unlanding-complaint-modal'>
<i class='iconfont icon-close close'></i>
<div class='header'>
登录提示
</div>
<div class='container actions'>
<div class='content'>
该操作需登录 Gitee 帐号，请先登录后再操作。
</div>
<div class='ui orange icon large button ok'>
立即登录
</div>
<div class='ui button blank cancel'>
没有帐号，去注册
</div>
</div>
</div>
<script>
  var $elm = $('.download');
  
  $elm.on('click', function() {
    var modals = $("#unlanding-complaint-modal.download_repository_zip");
    if (modals.length > 1) {
      modals.eq(0).modal('show');
    } else {
      modals.modal('show');
    }
  })
  $("#unlanding-complaint-modal.download_repository_zip").modal({
    onDeny: function() {
      window.location.href = "/signup?from=download_repository_zip";
    },
    onApprove: function() {
      window.location.href = "/login?from=download_repository_zip";
    }
  })
</script>

</div>
<script>
  (function() {
    var $btnClone, $btnCopy, $input, $panel;
  
    $btnClone = $('#btn-dl-or-clone');
  
    $panel = $('.git-project-download-panel');
  
    $input = $('#project_clone_url');
  
    $btnCopy = $('#btn-copy-clone-url');
  
    $btnClone.popup({
      on: 'click',
      hoverable: true,
      position: 'bottom center'
    });
  
    $panel.find('.menu > .item').on('click', function(e) {
      var $item, dataUrl;
      $item = $(this).addClass('active');
      $item.siblings().removeClass('active');
      dataUrl = $item.attr('data-url');
      if (dataUrl) {
        $panel.find('.download-url-panel').show();
        $input.val(dataUrl);
        $panel.find('.forbid-warning-text').html('');
      } else {
        $panel.find('.download-url-panel').hide();
        $panel.find('.forbid-warning-text').html($item.attr('data-text') || '');
      }
      return $.cookie('remote_way', $item.attr('data-type'), {
        expires: 365,
        path: '/'
      });
    }).filter('[data-type="' + ($.cookie('remote_way') || 'http') + '"]').trigger('click');
  
    new Clipboard($btnCopy[0]).on('success', function() {
      $btnCopy.popup({
        content: '已复制',
        position: 'right center',
        onHidden: function() {
          return $btnCopy.popup('destroy');
        }
      });
      return $btnCopy.popup('show');
    });
  
  }).call(this);
</script>

</div>
<div class='d-inline pull-right' id='git-project-root-actions'>
<script>
  $('.disabled-upload-readonly').popup({
    content: "只读目录不允许上传文件",
    className: {
      popup: 'ui popup',
    },
    position: 'bottom center',
  })
  $('.disabled-create-folder').popup({
    content: "只读目录不允许创建目录",
    className: {
      popup: 'ui popup',
    },
    position: 'bottom center',
  })
  $('.disabled-create-file').popup({
    content: "只读目录不允许创建文件",
    className: {
      popup: 'ui popup',
    },
    position: 'bottom center',
  })
  $('.disabled-create-submodule').popup({
    content: "只读目录不允许创建子模块",
    className: {
      popup: 'ui popup',
    },
    position: 'bottom center',
  })
  $('.disabled-upload-readonly, .disabled-create-folder, .disabled-create-file, .disabled-create-submodule').click(function() {
    return false
  })
</script>
<style>
  .disabled-upload-readonly, .disabled-create-file, .disabled-create-folder, .disabled-create-submodule {
    background-color: #dcddde !important;
    color: rgba(0, 0, 0, 0.4) !important;
    opacity: 0.3 !important;
    background-image: none !important;
    -webkit-box-shadow: none !important;
            box-shadow: none !important; }
</style>


</div>
<div class='breadcrumb_path path-breadcrumb-contrainer' id='git-project-breadcrumb'>
<div class='ui breadcrumb path project-path-breadcrumb' id='path-breadcrumb'>
<a data-direction="back" class="section repo-name" style="font-weight: bold" href="/xuxueli0323/xxl-job/tree/master">xxl-job
</a><div class='divider'>
/
</div>
<strong>
<a data-direction="back" class="section" href="/xuxueli0323/xxl-job/tree/master/doc"><span class='cblue'>
doc
</span>
</a></strong>
<div class='divider'>
/
</div>
<strong>
XXL-JOB官方文档.md
</strong>
<i class='iconfont icon-clone' data-clipboard-text='doc/XXL-JOB官方文档.md' id='btn-copy-file-path'></i>
</div>
<style>
  #btn-copy-file-path {
    vertical-align: middle;
    cursor: pointer;
  }
</style>
<script>
  $btnCopy = $('#btn-copy-file-path')
  $btnCopy.popup({
    content: '复制路径'
  })
  
  if ($btnCopy[0]) {
    new Clipboard($btnCopy[0]).on('success', function() {
      $btnCopy.popup('destroy').popup({
        content: '已复制',
        on: 'manual'
      }).popup('show');
      setTimeout(function () {
        $btnCopy.popup('destroy').popup({
          content: '复制路径'
        });
      }, 2000)
    });
  }
</script>


</div>
<div class='ui horizontal list repo-action-list branches-tags' style='display: none;'>
<div class='item'>
<a class="ui blank button" href="/xuxueli0323/xxl-job/branches"><i class='iconfont icon-branches'></i>
分支 14
</a></div>
<div class='item mr-3'>
<a class="ui blank button" href="/xuxueli0323/xxl-job/tags"><i class='iconfont icon-tag'></i>
标签 31
</a></div>
</div>
</div>
<script>
  if(window.gon.locale == 'en')
    $('.branches-tags').css('margin-top', '12px')
</script>

<style>
  .ui.dropdown .menu > .header {
    text-transform: none; }
</style>
<script>
  $(function () {
    var $tip = $('#apk-download-tip');
    if (!$tip.length) {
      return;
    }
    $tip.find('.btn-close').on('click', function () {
      $tip.hide();
    });
  });
  (function(){
    function pathAutoRender() {
      var $parent = $('#git-project-bread'),
          $child = $('#git-project-bread').children('.ui.horizontal.list'),
          mainWidth = 0;
      $child.each(function (i,item) {
        mainWidth += $(item).width()
      });
      $('.breadcrumb.path.fork-path').remove();
      if (mainWidth > 995) {
        $('#path-breadcrumb').hide();
        $parent.append('<div class="ui breadcrumb path fork-path">' + $('#path-breadcrumb').html() + '<div/>')
      } else {
        $('#path-breadcrumb').show();
      }
    }
    window.pathAutoRender = pathAutoRender;
    pathAutoRender();
  })();
</script>

<div class='row column tree-holder' id='tree-holder'>
<div class='tree-content-holder' id='tree-content-holder'>
<div class='file_holder'>
<div class='file_title'>
<div class='blob-header-title'>
<div class='blob-description'>
<i class="iconfont icon-file"></i>
<span class='file_name' title='XXL-JOB官方文档.md'>
XXL-JOB官方文档.md
</span>
<small>142.08 KB</small>
</div>
<div class='options'><div class='ui mini buttons basic'>
<textarea name="blob_raw" id="blob_raw" style="display:none;">
## 《分布式任务调度平台XXL-JOB》&#x000A;&#x000A;[![Actions Status](https://github.com/xuxueli/xxl-job/workflows/Java%20CI/badge.svg)](https://github.com/xuxueli/xxl-job/actions)&#x000A;[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.xuxueli/xxl-job/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.xuxueli/xxl-job/)&#x000A;[![GitHub release](https://img.shields.io/github/release/xuxueli/xxl-job.svg)](https://github.com/xuxueli/xxl-job/releases)&#x000A;[![GitHub stars](https://img.shields.io/github/stars/xuxueli/xxl-job)](https://github.com/xuxueli/xxl-job/)&#x000A;[![Docker Status](https://img.shields.io/docker/pulls/xuxueli/xxl-job-admin)](https://hub.docker.com/r/xuxueli/xxl-job-admin/)&#x000A;[![License](https://img.shields.io/badge/license-GPLv3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0.html)&#x000A;[![donate](https://img.shields.io/badge/%24-donate-ff69b4.svg?style=flat)](https://www.xuxueli.com/page/donate.html)&#x000A;&#x000A;[TOCM]&#x000A;&#x000A;[TOC]&#x000A;&#x000A;## 一、简介&#x000A;&#x000A;### 1.1 概述&#x000A;XXL-JOB是一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。&#x000A;&#x000A;### 1.2 社区交流    &#x000A;- [社区交流](https://www.xuxueli.com/page/community.html)&#x000A;&#x000A;### 1.3 特性&#x000A;- 1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；&#x000A;- 2、动态：支持动态修改任务状态、启动/停止任务，以及终止运行中任务，即时生效；&#x000A;- 3、调度中心HA（中心式）：调度采用中心式设计，“调度中心”自研调度组件并支持集群部署，可保证调度中心HA；&#x000A;- 4、执行器HA（分布式）：任务分布式执行，任务&quot;执行器&quot;支持集群部署，可保证任务执行HA；&#x000A;- 5、注册中心: 执行器会周期性自动注册任务, 调度中心将会自动发现注册的任务并触发执行。同时，也支持手动录入执行器地址；&#x000A;- 6、弹性扩容缩容：一旦有新执行器机器上线或者下线，下次调度时将会重新分配任务；&#x000A;- 7、触发策略：提供丰富的任务触发策略，包括：Cron触发、固定间隔触发、固定延时触发、API（事件）触发、人工触发、父子任务触发；&#x000A;- 8、调度过期策略：调度中心错过调度时间的补偿处理策略，包括：忽略、立即补偿触发一次等；&#x000A;- 9、阻塞处理策略：调度过于密集执行器来不及处理时的处理策略，策略包括：单机串行（默认）、丢弃后续调度、覆盖之前调度；&#x000A;- 10、任务超时控制：支持自定义任务超时时间，任务运行超时将会主动中断任务；&#x000A;- 11、任务失败重试：支持自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；其中分片任务支持分片粒度的失败重试；&#x000A;- 12、任务失败告警；默认提供邮件方式失败告警，同时预留扩展接口，可方便的扩展短信、钉钉等告警方式；&#x000A;- 13、路由策略：执行器集群部署时提供丰富的路由策略，包括：第一个、最后一个、轮询、随机、一致性HASH、最不经常使用、最近最久未使用、故障转移、忙碌转移等；&#x000A;- 14、分片广播任务：执行器集群部署时，任务路由策略选择&quot;分片广播&quot;情况下，一次任务调度将会广播触发集群中所有执行器执行一次任务，可根据分片参数开发分片任务；&#x000A;- 15、动态分片：分片广播任务以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。&#x000A;- 16、故障转移：任务路由策略选择&quot;故障转移&quot;情况下，如果执行器集群中某一台机器故障，将会自动Failover切换到一台正常的执行器发送调度请求。&#x000A;- 17、任务进度监控：支持实时监控任务进度；&#x000A;- 18、Rolling实时日志：支持在线查看调度结果，并且支持以Rolling方式实时查看执行器输出的完整的执行日志；&#x000A;- 19、GLUE：提供Web IDE，支持在线开发任务逻辑代码，动态发布，实时编译生效，省略部署上线的过程。支持30个版本的历史版本回溯。&#x000A;- 20、脚本任务：支持以GLUE模式开发和运行脚本任务，包括Shell、Python、NodeJS、PHP、PowerShell等类型脚本;&#x000A;- 21、命令行任务：原生提供通用命令行任务Handler（Bean任务，&quot;CommandJobHandler&quot;）；业务方只需要提供命令行即可；&#x000A;- 22、任务依赖：支持配置子任务依赖，当父任务执行结束且执行成功后将会主动触发一次子任务的执行, 多个子任务用逗号分隔；&#x000A;- 23、一致性：“调度中心”通过DB锁保证集群分布式调度的一致性, 一次任务调度只会触发一次执行；&#x000A;- 24、自定义任务参数：支持在线配置调度任务入参，即时生效；&#x000A;- 25、调度线程池：调度系统多线程触发调度运行，确保调度精确执行，不被堵塞；&#x000A;- 26、数据加密：调度中心和执行器之间的通讯进行数据加密，提升调度信息安全性；&#x000A;- 27、邮件报警：任务失败时支持邮件报警，支持配置多邮件地址群发报警邮件；&#x000A;- 28、推送maven中央仓库: 将会把最新稳定版推送到maven中央仓库, 方便用户接入和使用;&#x000A;- 29、运行报表：支持实时查看运行数据，如任务数量、调度次数、执行器数量等；以及调度报表，如调度日期分布图，调度成功分布图等；&#x000A;- 30、全异步：任务调度流程全异步化设计实现，如异步调度、异步运行、异步回调等，有效对密集调度进行流量削峰，理论上支持任意时长任务的运行；&#x000A;- 31、跨语言：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。除此之外，还提供了 “多任务模式”和“httpJobHandler”等其他跨语言方案；&#x000A;- 32、国际化：调度中心支持国际化设置，提供中文、英文两种可选语言，默认为中文；&#x000A;- 33、容器化：提供官方docker镜像，并实时更新推送dockerhub，进一步实现产品开箱即用；&#x000A;- 34、线程池隔离：调度线程池进行隔离拆分，慢任务自动降级进入&quot;Slow&quot;线程池，避免耗尽调度线程，提高系统稳定性；&#x000A;- 35、用户管理：支持在线管理系统用户，存在管理员、普通用户两种角色；&#x000A;- 36、权限控制：执行器维度进行权限控制，管理员拥有全量权限，普通用户需要分配执行器权限后才允许相关操作；&#x000A;&#x000A;### 1.4 发展&#x000A;于2015年中，我在github上创建XXL-JOB项目仓库并提交第一个commit，随之进行系统结构设计，UI选型，交互设计……&#x000A;&#x000A;于2015-11月，XXL-JOB终于RELEASE了第一个大版本V1.0， 随后我将之发布到OSCHINA，XXL-JOB在OSCHINA上获得了@红薯的热门推荐，同期分别达到了OSCHINA的“热门动弹”排行第一和git.oschina的开源软件月热度排行第一，在此特别感谢红薯，感谢大家的关注和支持。&#x000A;&#x000A;于2015-12月，我将XXL-JOB发表到我司内部知识库，并且得到内部同事认可。&#x000A;&#x000A;于2016-01月，我司展开XXL-JOB的内部接入和定制工作，在此感谢袁某和尹某两位同事的贡献，同时也感谢内部其他给与关注与支持的同事。&#x000A;&#x000A;于2017-05-13，在上海举办的 &quot;[第62期开源中国源创会](https://www.oschina.net/event/2236961)&quot; 的 &quot;放码过来&quot; 环节，我登台对XXL-JOB做了演讲，台下五百位在场观众反响热烈（[图文回顾](https://www.oschina.net/question/2686220_2242120) ）。&#x000A;&#x000A;于2017-10-22，又拍云 Open Talk 联合 Spring Cloud 中国社区举办的 &quot;[进击的微服务实战派上海站](https://opentalk.upyun.com/303.html)&quot;，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。&#x000A;&#x000A;于2017-12-11，XXL-JOB有幸参会《[InfoQ ArchSummit全球架构师峰会](http://bj2017.archsummit.com/)》，并被拍拍贷架构总监&quot;杨波老师&quot;在专题 &quot;[微服务原理、基础架构和开源实践](http://bj2017.archsummit.com/training/2)&quot; 中现场介绍。&#x000A;&#x000A;于2017-12-18，XXL-JOB参与&quot;[2017年度最受欢迎中国开源软件](http://www.oschina.net/project/top_cn_2017?sort=1)&quot;评比，在当时已录入的约九千个国产开源项目中角逐，最终进入了前30强。&#x000A;&#x000A;于2018-01-15，XXL-JOB参与&quot;[2017码云最火开源项目](https://www.oschina.net/news/92438/2017-mayun-top-50)&quot;评比，在当时已录入的约六千五百个码云项目中角逐，最终进去了前20强。&#x000A;&#x000A;于2018-04-14，iTechPlus在上海举办的 &quot;[2018互联网开发者大会](http://www.itdks.com/eventlist/detail/2065)&quot;，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。&#x000A;&#x000A;于2018-05-27，在上海举办的 &quot;[第75期开源中国源创会](https://www.oschina.net/event/2278742)&quot; 的 &quot;架构&quot; 主题专场，我登台进行“基础架构与中间件图谱”主题演讲，台下上千位在场观众反响热烈（[图文回顾](https://www.oschina.net/question/3802184_2280606) ）。&#x000A;&#x000A;于2018-12-05，XXL-JOB参与&quot;[2018年度最受欢迎中国开源软件](https://www.oschina.net/project/top_cn_2018?sort=1)&quot;评比，在当时已录入的一万多个开源项目中角逐，最终排名第19名。&#x000A;&#x000A;于2019-12-10，XXL-JOB参与&quot;[2019年度最受欢迎中国开源软件](https://www.oschina.net/project/top_cn_2019)&quot;评比，在当时已录入的一万多个开源项目中角逐，最终排名&quot;开发框架和基础组件类&quot;第9名。&#x000A;&#x000A;于2020-11-16，XXL-JOB参与&quot;[2020年度最受欢迎中国开源软件](https://www.oschina.net/project/top_cn_2020)&quot;评比，在当时已录入的一万多个开源项目中角逐，最终排名&quot;开发框架和基础组件类&quot;第8名。&#x000A;&#x000A;于2021-12-06，XXL-JOB参与&quot;[2021年度OSC中国开源项目评选](https://www.oschina.net/project/top_cn_2021) &quot;评比，在当时已录入的一万多个开源项目中角逐，最终当选&quot;最受欢迎项目&quot;。&#x000A;&#x000A;&gt; 我司大众点评目前已接入XXL-JOB，内部别名《Ferrari》（Ferrari基于XXL-JOB的V1.1版本定制而成，新接入应用推荐升级最新版本）。&#x000A;据最新统计, 自2016-01-21接入至2017-12-01期间，该系统已调度约100万次，表现优异。新接入应用推荐使用最新版本，因为经过数十个版本的更新，系统的任务模型、UI交互模型以及底层调度通讯模型都有了较大的优化和提升，核心功能更加稳定高效。&#x000A;&#x000A;至今，XXL-JOB已接入多家公司的线上产品线，接入场景如电商业务，O2O业务和大数据作业等，截止最新统计时间为止，XXL-JOB已接入的公司包括不限于：&#x000A;&#x000A;	- 1、大众点评【美团点评】&#x000A;	- 2、山东学而网络科技有限公司；&#x000A;	- 3、安徽慧通互联科技有限公司；&#x000A;	- 4、人人聚财金服；&#x000A;	- 5、上海棠棣信息科技股份有限公司&#x000A;	- 6、运满满【运满满】&#x000A;	- 7、米其林 (中国区)【米其林】&#x000A;	- 8、妈妈联盟&#x000A;	- 9、九樱天下（北京）信息技术有限公司&#x000A;	- 10、万普拉斯科技有限公司【一加手机】&#x000A;	- 11、上海亿保健康管理有限公司&#x000A;	- 12、海尔馨厨【海尔】&#x000A;	- 13、河南大红包电子商务有限公司&#x000A;	- 14、成都顺点科技有限公司&#x000A;	- 15、深圳市怡亚通&#x000A;	- 16、深圳麦亚信科技股份有限公司&#x000A;	- 17、上海博莹科技信息技术有限公司&#x000A;	- 18、中国平安科技有限公司【中国平安】&#x000A;	- 19、杭州知时信息科技有限公司&#x000A;	- 20、博莹科技（上海）有限公司&#x000A;	- 21、成都依能股份有限责任公司&#x000A;	- 22、湖南高阳通联信息技术有限公司&#x000A;	- 23、深圳市邦德文化发展有限公司&#x000A;	- 24、福建阿思可网络教育有限公司&#x000A;	- 25、优信二手车【优信】&#x000A;	- 26、上海悠游堂投资发展股份有限公司【悠游堂】&#x000A;	- 27、北京粉笔蓝天科技有限公司&#x000A;	- 28、中秀科技(无锡)有限公司&#x000A;	- 29、武汉空心科技有限公司&#x000A;	- 30、北京蚂蚁风暴科技有限公司&#x000A;	- 31、四川互宜达科技有限公司&#x000A;	- 32、钱包行云（北京）科技有限公司&#x000A;	- 33、重庆欣才集团&#x000A;    - 34、咪咕互动娱乐有限公司【中国移动】&#x000A;    - 35、北京诺亦腾科技有限公司&#x000A;    - 36、增长引擎(北京)信息技术有限公司&#x000A;    - 37、北京英贝思科技有限公司&#x000A;    - 38、刚泰集团&#x000A;    - 39、深圳泰久信息系统股份有限公司&#x000A;    - 40、随行付支付有限公司&#x000A;    - 41、广州瀚农网络科技有限公司&#x000A;    - 42、享点科技有限公司&#x000A;    - 43、杭州比智科技有限公司&#x000A;    - 44、圳临界线网络科技有限公司&#x000A;    - 45、广州知识圈网络科技有限公司&#x000A;    - 46、国誉商业上海有限公司&#x000A;    - 47、海尔消费金融有限公司，嗨付、够花【海尔】&#x000A;    - 48、广州巴图鲁信息科技有限公司&#x000A;    - 49、深圳市鹏海运电子数据交换有限公司&#x000A;    - 50、深圳市亚飞电子商务有限公司&#x000A;    - 51、上海趣医网络有限公司&#x000A;    - 52、聚金资本&#x000A;    - 53、北京父母邦网络科技有限公司&#x000A;    - 54、中山元赫软件科技有限公司&#x000A;    - 55、中商惠民(北京)电子商务有限公司&#x000A;    - 56、凯京集团&#x000A;    - 57、华夏票联（北京）科技有限公司&#x000A;    - 58、拍拍贷【拍拍贷】&#x000A;    - 59、北京尚德机构在线教育有限公司&#x000A;    - 60、任子行股份有限公司&#x000A;    - 61、北京时态电子商务有限公司&#x000A;    - 62、深圳卷皮网络科技有限公司&#x000A;    - 63、北京安博通科技股份有限公司&#x000A;    - 64、未来无线网&#x000A;    - 65、厦门瓷禧网络有限公司&#x000A;    - 66、北京递蓝科软件股份有限公司&#x000A;    - 67、郑州创海软件科技公司&#x000A;    - 68、北京国槐信息科技有限公司&#x000A;    - 69、浪潮软件集团&#x000A;    - 70、多立恒(北京)信息技术有限公司&#x000A;    - 71、广州极迅客信息科技有限公司&#x000A;    - 72、赫基（中国）集团股份有限公司&#x000A;    - 73、海投汇&#x000A;    - 74、上海润益创业孵化器管理股份有限公司&#x000A;    - 75、汉纳森（厦门）数据股份有限公司&#x000A;    - 76、安信信托&#x000A;    - 77、岚儒财富&#x000A;    - 78、捷道软件&#x000A;    - 79、湖北享七网络科技有限公司&#x000A;    - 80、湖南创发科技责任有限公司&#x000A;    - 81、深圳小安时代互联网金融服务有限公司&#x000A;    - 82、湖北享七网络科技有限公司&#x000A;    - 83、钱包行云(北京)科技有限公司&#x000A;    - 84、360金融【360】&#x000A;    - 85、易企秀&#x000A;    - 86、摩贝（上海）生物科技有限公司&#x000A;    - 87、广东芯智慧科技有限公司&#x000A;    - 88、联想集团【联想】&#x000A;    - 89、怪兽充电&#x000A;    - 90、行圆汽车&#x000A;    - 91、深圳店店通科技邮箱公司&#x000A;    - 92、京东【京东】&#x000A;    - 93、米庄理财&#x000A;    - 94、咖啡易融&#x000A;    - 95、梧桐诚选&#x000A;    - 96、恒大地产【恒大】&#x000A;    - 97、昆明龙慧&#x000A;    - 98、上海涩瑶软件&#x000A;    - 99、易信【网易】&#x000A;    - 100、铜板街&#x000A;    - 101、杭州云若网络科技有限公司&#x000A;    - 102、特百惠（中国）有限公司&#x000A;    - 103、常山众卡运力供应链管理有限公司&#x000A;    - 104、深圳立创电子商务有限公司&#x000A;    - 105、杭州智诺科技股份有限公司&#x000A;    - 106、北京云漾信息科技有限公司&#x000A;    - 107、深圳市多银科技有限公司&#x000A;    - 108、亲宝宝&#x000A;    - 109、上海博卡软件科技有限公司&#x000A;    - 110、智慧树在线教育平台&#x000A;    - 111、米族金融&#x000A;    - 112、北京辰森世纪&#x000A;    - 113、云南滇医通&#x000A;    - 114、广州市分领网络科技有限责任公司&#x000A;    - 115、浙江微能科技有限公司&#x000A;    - 116、上海馨飞电子商务有限公司&#x000A;    - 117、上海宝尊电子商务有限公司&#x000A;    - 118、直客通科技技术有限公司&#x000A;    - 119、科度科技有限公司&#x000A;    - 120、上海数慧系统技术有限公司&#x000A;    - 121、我的医药网&#x000A;    - 122、多粉平台&#x000A;    - 123、铁甲二手机&#x000A;    - 124、上海海新得数据技术有限公司&#x000A;    - 125、深圳市珍爱网信息技术有限公司【珍爱网】&#x000A;    - 126、小蜜蜂&#x000A;    - 127、吉荣数科技&#x000A;    - 128、上海恺域信息科技有限公司&#x000A;    - 129、广州荔支网络有限公司【荔枝FM】&#x000A;    - 130、杭州闪宝科技有限公司&#x000A;    - 131、北京互联新网科技发展有限公司&#x000A;    - 132、誉道科技&#x000A;    - 133、山西兆盛房地产开发有限公司&#x000A;    - 134、北京蓝睿通达科技有限公司&#x000A;    - 135、月亮小屋（中国）有限公司【蓝月亮】&#x000A;    - 136、青岛国瑞信息技术有限公司&#x000A;    - 137、博雅云计算（北京）有限公司&#x000A;    - 138、华泰证券香港子公司&#x000A;    - 139、杭州东方通信软件技术有限公司&#x000A;    - 140、武汉博晟安全技术股份有限公司&#x000A;    - 141、深圳市六度人和科技有限公司&#x000A;    - 142、杭州趣维科技有限公司（小影）&#x000A;    - 143、宁波单车侠之家科技有限公司【单车侠】&#x000A;    - 144、丁丁云康信息科技（北京）有限公司&#x000A;    - 145、云钱袋&#x000A;    - 146、南京中兴力维&#x000A;    - 147、上海矽昌通信技术有限公司&#x000A;    - 148、深圳萨科科技&#x000A;    - 149、中通服创立科技有限责任公司&#x000A;    - 150、深圳市对庄科技有限公司&#x000A;    - 151、上证所信息网络有限公司&#x000A;    - 152、杭州火烧云科技有限公司【婚礼纪】&#x000A;    - 153、天津青芒果科技有限公司【芒果头条】&#x000A;    - 154、长飞光纤光缆股份有限公司&#x000A;    - 155、世纪凯歌（北京）医疗科技有限公司&#x000A;    - 156、浙江霖梓控股有限公司&#x000A;    - 157、江西腾飞网络技术有限公司&#x000A;    - 158、安迅物流有限公司&#x000A;    - 159、肉联网&#x000A;    - 160、北京北广梯影广告传媒有限公司&#x000A;    - 161、上海数慧系统技术有限公司&#x000A;    - 162、大志天成&#x000A;    - 163、上海云鹊医&#x000A;    - 164、上海云鹊医&#x000A;    - 165、墨迹天气【墨迹天气】&#x000A;    - 166、上海逸橙信息科技有限公司&#x000A;    - 167、沅朋物联&#x000A;    - 168、杭州恒生云融网络科技有限公司&#x000A;    - 169、绿米联创&#x000A;    - 170、重庆易宠科技有限公司&#x000A;    - 171、安徽引航科技有限公司（乐职网）&#x000A;    - 172、上海数联医信企业发展有限公司&#x000A;    - 173、良彬建材&#x000A;    - 174、杭州求是同创网络科技有限公司&#x000A;    - 175、荷马国际&#x000A;    - 176、点雇网&#x000A;    - 177、深圳市华星光电技术有限公司&#x000A;    - 178、厦门神州鹰软件科技有限公司&#x000A;    - 179、深圳市招商信诺人寿保险有限公司&#x000A;    - 180、上海好屋网信息技术有限公司&#x000A;    - 181、海信集团【海信】&#x000A;    - 182、信凌可信息科技（上海）有限公司&#x000A;    - 183、长春天成科技发展有限公司&#x000A;    - 184、用友金融信息技术股份有限公司【用友】&#x000A;    - 185、北京咖啡易融有限公司&#x000A;    - 186、国投瑞银基金管理有限公司&#x000A;    - 187、晋松(上海)网络信息技术有限公司&#x000A;    - 188、深圳市随手科技有限公司【随手记】&#x000A;    - 189、深圳水务科技有限公司&#x000A;    - 190、易企秀【易企秀】&#x000A;    - 191、北京磁云科技&#x000A;    - 192、南京蜂泰互联网科技有限公司&#x000A;    - 193、章鱼直播&#x000A;    - 194、奖多多科技&#x000A;    - 195、天津市神州商龙科技股份有限公司&#x000A;    - 196、岩心科技&#x000A;    - 197、车码科技（北京）有限公司&#x000A;    - 198、贵阳市投资控股集团&#x000A;    - 199、康旗股份&#x000A;    - 200、龙腾出行&#x000A;    - 201、杭州华量软件&#x000A;    - 202、合肥顶岭医疗科技有限公司&#x000A;    - 203、重庆表达式科技有限公司&#x000A;    - 204、上海米道信息科技有限公司&#x000A;    - 205、北京益友会科技有限公司&#x000A;    - 206、北京融贯电子商务有限公司&#x000A;    - 207、中国外汇交易中心&#x000A;    - 208、中国外运股份有限公司&#x000A;    - 209、中国上海晓圈教育科技有限公司&#x000A;    - 210、普联软件股份有限公司&#x000A;    - 211、北京科蓝软件股份有限公司&#x000A;    - 212、江苏斯诺物联科技有限公司&#x000A;    - 213、北京搜狐-狐友【搜狐】&#x000A;    - 214、新大陆网商金融&#x000A;    - 215、山东神码中税信息科技有限公司&#x000A;    - 216、河南汇顺网络科技有限公司&#x000A;    - 217、北京华夏思源科技发展有限公司&#x000A;    - 218、上海东普信息科技有限公司&#x000A;    - 219、上海鸣勃网络科技有限公司&#x000A;    - 220、广东学苑教育发展有限公司&#x000A;    - 221、深圳强时科技有限公司&#x000A;    - 222、上海云砺信息科技有限公司&#x000A;    - 223、重庆愉客行网络有限公司&#x000A;    - 224、数云&#x000A;    - 225、国家电网运检部&#x000A;    - 226、杭州找趣&#x000A;    - 227、浩鲸云计算科技股份有限公司&#x000A;    - 228、科大讯飞【科大讯飞】&#x000A;    - 229、杭州行装网络科技有限公司&#x000A;    - 230、即有分期金融&#x000A;    - 231、深圳法司德信息科技有限公司&#x000A;    - 232、上海博复信息科技有限公司&#x000A;    - 233、杭州云嘉云计算有限公司&#x000A;    - 234、有家民宿(有家美宿)&#x000A;    - 235、北京赢销通软件技术有限公司&#x000A;    - 236、浙江聚有财金融服务外包有限公司&#x000A;    - 237、易族智汇(北京)科技有限公司&#x000A;    - 238、合肥顶岭医疗科技开发有限公司&#x000A;    - 239、车船宝(深圳)旭珩科技有限公司)&#x000A;    - 240、广州富力地产有限公司&#x000A;    - 241、氢课（上海）教育科技有限公司&#x000A;    - 242、武汉氪细胞网络技术有限公司&#x000A;    - 243、杭州有云科技有限公司&#x000A;    - 244、上海仙豆智能机器人有限公司&#x000A;    - 245、拉卡拉支付股份有限公司【拉卡拉】&#x000A;    - 246、虎彩印艺股份有限公司&#x000A;    - 247、北京数微科技有限公司&#x000A;    - 248、广东智瑞科技有限公司&#x000A;    - 249、找钢网&#x000A;    - 250、九机网&#x000A;    - 251、杭州跑跑网络科技有限公司&#x000A;    - 252、深圳未来云集&#x000A;    - 253、杭州每日给力科技有限公司&#x000A;    - 254、上海齐犇信息科技有限公司&#x000A;    - 255、滴滴出行【滴滴】&#x000A;    - 256、合肥云诊信息科技有限公司&#x000A;    - 257、云知声智能科技股份有限公司&#x000A;    - 258、南京坦道科技有限公司&#x000A;    - 259、爱乐优（二手平台）&#x000A;    - 260、猫眼电影（私有化部署）【猫眼电影】&#x000A;    - 261、美团大象（私有化部署）【美团大象】&#x000A;    - 262、作业帮教育科技（北京）有限公司【作业帮】&#x000A;    - 263、北京小年糕互联网技术有限公司&#x000A;    - 264、山东矩阵软件工程股份有限公司&#x000A;    - 265、陕西国驿软件科技有限公司&#x000A;    - 266、君开信息科技&#x000A;    - 267、村鸟网络科技有限责任公司&#x000A;    - 268、云南国际信托有限公司&#x000A;    - 269、金智教育&#x000A;    - 270、珠海市筑巢科技有限公司&#x000A;    - 271、上海百胜软件股份有限公司&#x000A;    - 272、深圳市科盾科技有限公司&#x000A;    - 273、哈啰出行【哈啰】&#x000A;    - 274、途虎养车【途虎】&#x000A;    - 275、卡思优派人力资源集团&#x000A;    - 276、南京观为智慧软件科技有限公司&#x000A;    - 277、杭州城市大脑科技有限公司&#x000A;    - 278、猿辅导【猿辅导】&#x000A;    - 279、洛阳健创网络科技有限公司&#x000A;    - 280、魔力耳朵&#x000A;    - 281、亿阳信通&#x000A;    - 282、上海招鲤科技有限公司&#x000A;    - 283、四川商旅无忧科技服务有限公司&#x000A;    - 284、UU跑腿&#x000A;    - 285、北京老虎证券【老虎证券】&#x000A;    - 286、悠活省吧（北京）网络科技有限公司&#x000A;    - 287、F5未来商店&#x000A;    - 288、深圳环阳通信息技术有限公司&#x000A;    - 289、遠傳電信&#x000A;    - 290、作业帮（北京）教育科技有限公司【作业帮】&#x000A;    - 291、成都科鸿智信科技有限公司&#x000A;    - 292、北京木屋时代科技有限公司&#x000A;    - 293、大学通（哈尔滨）科技有限责任公司&#x000A;    - 294、浙江华坤道威数据科技有限公司&#x000A;    - 295、吉祥航空【吉祥航空】&#x000A;    - 296、南京圆周网络科技有限公司&#x000A;    - 297、广州市洋葱omall电子商务&#x000A;    - 298、天津联物科技有限公司&#x000A;    - 299、跑哪儿科技（北京）有限公司&#x000A;    - 300、深圳市美西西餐饮有限公司(喜茶)&#x000A;    - 301、平安不动产有限公司【平安】&#x000A;    - 302、江苏中海昇物联科技有限公司&#x000A;    - 303、湖南牙医帮科技有限公司&#x000A;    - 304、重庆民航凯亚信息技术有限公司（易通航）&#x000A;    - 305、递易（上海）智能科技有限公司&#x000A;    - 306、亚朵&#x000A;    - 307、浙江新课堂教育股份有限公司&#x000A;    - 308、北京蜂创科技有限公司&#x000A;    - 309、德一智慧城市信息系统有限公司&#x000A;    - 310、北京翼点科技有限公司&#x000A;    - 311、湖南智数新维度信息科技有限公司&#x000A;    - 312、北京玖扬博文文化发展有限公司&#x000A;    - 313、上海宇珩信息科技有限公司&#x000A;    - 314、全景智联（武汉）科技有限公司&#x000A;    - 315、天津易客满国际物流有限公司&#x000A;    - 316、南京爱福路汽车科技有限公司&#x000A;    - 317、我房旅居集团&#x000A;    - 318、湛江亲邻科技有限公司&#x000A;    - 319、深圳市姜科网络有限公司&#x000A;    - 320、青岛日日顺物流有限公司&#x000A;    - 321、南京太川信息技术有限公司&#x000A;    - 322、美图之家科技优先公司【美图】&#x000A;    - 323、南京太川信息技术有限公司&#x000A;    - 324、众薪科技（北京）有限公司&#x000A;    - 325、武汉安安物联科技有限公司&#x000A;    - 326、北京智客朗道网络科技有限公司&#x000A;    - 327、深圳市超级猩猩健身管理管理有限公司&#x000A;    - 328、重庆达志科技有限公司&#x000A;    - 329、上海享评信息科技有限公司&#x000A;    - 330、薪得付信息科技&#x000A;    - 331、跟谁学&#x000A;    - 332、中道（苏州）旅游网络科技有限公司&#x000A;    - 333、广州小卫科技有限公司&#x000A;    - 334、上海非码网络科技有限公司&#x000A;    - 335、途家网网络技术（北京）有限公司【途家】&#x000A;    - 336、广州辉凡信息科技有限公司&#x000A;    - 337、天维尔信息科技股份有限公司&#x000A;    - 338、上海极豆科技有限公司&#x000A;    - 339、苏州触达信息技术有限公司&#x000A;    - 340、北京热云科技有限公司&#x000A;    - 341、中智企服（北京）科技有限公司&#x000A;    - 342、易联云计算（杭州）有限责任公司&#x000A;    - 343、青岛航空股份有限公司【青岛航空】&#x000A;    - 344、山西博睿通科技有限公司&#x000A;    - 345、网易杭州网络有限公司【网易】&#x000A;    - 346、北京果果乐学科技有限公司&#x000A;    - 347、百望股份有限公司&#x000A;    - 348、中保金服（深圳）科技有限公司&#x000A;    - 349、天津运友物流科技股份有限公司&#x000A;    - 350、广东创能科技股份有限公司&#x000A;    - 351、上海倚博信息科技有限公司&#x000A;    - 352、深圳百果园实业（集团）股份有限公司&#x000A;    - 353、广州细刻网络科技有限公司&#x000A;    - 354、武汉鸿业众创科技有限公司&#x000A;    - 355、金锡科技（广州）有限公司&#x000A;    - 356、易瑞国际电子商务有限公司&#x000A;    - 357、奇点云&#x000A;    - 358、中视信息科技有限公司&#x000A;    - 359、开源项目:datax-web&#x000A;    - 360、云知声智能科技股份有限公司&#x000A;    - 361、开源项目:bboss&#x000A;    - 362、成都深驾科技有限公司&#x000A;    - 363、FunPlus【趣加】&#x000A;    - 364、杭州创匠信科技有限公司&#x000A;    - 365、龙匠（北京）科技发展有限公司&#x000A;    - 366、广州一链通互联网科技有限公司&#x000A;    - 367、上海星艾网络科技有限公司&#x000A;    - 368、虎博网络技术(上海)有限公司&#x000A;    - 369、青岛优米信息技术有限公司&#x000A;    - 370、八维通科技有限公司&#x000A;    - 371、烟台合享智星数据科技有限公司&#x000A;    - 372、东吴证券股份有限公司&#x000A;    - 373、中通云仓股份有限公司【中通】&#x000A;    - 374、北京加菲猫科技有限公司&#x000A;    - 375、北京匠心演绎科技有限公司&#x000A;    - 376、宝贝走天下&#x000A;    - 377、厦门众库科技有限公司&#x000A;    - 378、海通证券数据中心&#x000A;    - 389、湖南快乐通宝小额贷款有限公司&#x000A;    - 380、浙江大华技术股份有限公司&#x000A;    - 381、杭州魔筷科技有限公司&#x000A;    - 382、青岛掌讯通区块链科技有限公司&#x000A;    - 383、新大陆金融科技&#x000A;    - 384、常州玺拓软件科技有限公司&#x000A;    - 385、北京正保网格教育科技有限公司&#x000A;    - 386、统一企业（中国）投资有限公司【统一】&#x000A;    - 387、微革网络科技有限公司&#x000A;    - 388、杭州融易算科技有限公司&#x000A;    - 399、青岛上啥班网络科技有限公司&#x000A;    - 390、京东酒世界&#x000A;    - 391、杭州爱博仕科技有限公司&#x000A;    - 392、五星金服控股有限公司&#x000A;    - 393、福建乐摩物联科技有限公司&#x000A;    - 394、百炼智能科技有限公司&#x000A;    - 395、山东能源数智云科技有限公司&#x000A;    - 396、招商局能源运输股份有限公司&#x000A;    - 397、三一集团【三一】&#x000A;    - 398、东巴文（深圳）健康管理有限公司&#x000A;    - 399、索易软件&#x000A;    - 400、深圳市宁远科技有限公司&#x000A;    - 401、熙牛医疗&#x000A;    - 402、南京智鹤电子科技有限公司&#x000A;    - 403、嘀嗒出行【嘀嗒出行】&#x000A;    - 404、广州虎牙信息科技有限公司【虎牙】&#x000A;    - 405、广州欧莱雅百库网络科技有限公司【欧莱雅】&#x000A;    - 406、微微科技有限公司&#x000A;    - 407、我爱我家房地产经纪有限公司【我爱我家】&#x000A;    - 408、九号发现&#x000A;    - 409、薪人薪事&#x000A;    - 410、武汉氪细胞网络技术有限公司&#x000A;    - 411、广州市斯凯奇商业有限公司&#x000A;    - 412、微淼商学院&#x000A;    - 413、杭州车盛科技有限公司&#x000A;    - 414、深兰科技（上海）有限公司&#x000A;    - 415、安徽中科美络信息技术有限公司&#x000A;    - 416、比亚迪汽车工业有限公司【比亚迪】&#x000A;    - 417、湖南小桔信息技术有限公司&#x000A;    - 418、安徽科大国创软件科技有限公司&#x000A;    - 419、克而瑞&#x000A;    - 420、陕西云基华海信息技术有限公司&#x000A;    - 421、安徽深宁科技有限公司&#x000A;    - 422、广东康爱多数字健康有限公司&#x000A;    - 423、嘉里电子商务&#x000A;    - 424、上海时代光华教育发展有限公司&#x000A;    - 425、CityDo&#x000A;    - 426、上海禹知信息科技有限公司&#x000A;    - 427、广东智瑞科技有限公司&#x000A;    - 428、西安爱铭网络科技有限公司&#x000A;    - 429、心医国际数字医疗系统(大连)有限公司&#x000A;    - 430、乐其电商&#x000A;    - 431、锐达科技&#x000A;    - 432、天津长城滨银汽车金融有限公司&#x000A;    - 433、代码网&#x000A;    - 434、东莞市东城乔伦软件开发工作室&#x000A;    - 435、浙江百应科技有限公司&#x000A;    - 436、上海力爱帝信息技术有限公司(Red E)&#x000A;    - 437、云徙科技有限公司&#x000A;    - 438、北京康智乐思网络科技有限公司【大姨吗APP】&#x000A;    - 439、安徽开元瞬视科技有限公司&#x000A;    - 440、立方&#x000A;    - 441、厦门纵行科技&#x000A;    - 442、乐山-菲尼克斯半导体有限公司&#x000A;    - 443、武汉光谷联合集团有限公司&#x000A;    - 444、上海金仕达软件科技有限公司&#x000A;    - 445、深圳易世通达科技有限公司&#x000A;    - 446、爱动超越人工智能科技（北京）有限责任公司&#x000A;    - 447、迪普信（北京）科技有限公司&#x000A;    - 448、掌站科技（北京）有限公司&#x000A;    - 449、深圳市华云中盛股份有限公司&#x000A;    - 450、上海原圈科技有限公司&#x000A;    - 451、广州赞赏信息科技有限公司&#x000A;    - 452、Amber Group&#x000A;    - 453、德威国际货运代理（上海）公司&#x000A;    - 454、浙江杰夫兄弟智慧科技有限公司&#x000A;    - 455、信也科技&#x000A;    - 456、开思时代科技（深圳）有限公司&#x000A;    - 457、大连槐德科技有限公司&#x000A;    - 458、同程生活&#x000A;    - 459、松果出行&#x000A;    - 460、企鹅杏仁集团&#x000A;    - 461、宁波科云信息科技有限公司&#x000A;    - 462、上海格蓝威驰信息科技有限公司&#x000A;    - 463、杭州趣淘鲸科技有限公司&#x000A;    - 464、湖州市数字惠民科技有限公司&#x000A;    - 465、乐普（北京）医疗器械股份有限公司&#x000A;    - 466、广州市晴川高新技术开发有限公司&#x000A;    - 467、山西缇客科技有限公司&#x000A;    - 468、徐州卡西穆电子商务有限公司&#x000A;    - 469、格创东智科技有限公司&#x000A;    - 470、世纪龙信息网络有限责任公司&#x000A;    - 471、邦道科技有限公司&#x000A;    - 472、河南中盟新云科技股份有限公司&#x000A;    - 473、横琴人寿保险有限公司&#x000A;    - 474、上海海隆华钟信息技术有限公司&#x000A;    - 475、上海久湛&#x000A;    - 476、上海仙豆智能机器人有限公司&#x000A;    - 477、广州汇尚网络科技有限公司&#x000A;    - 478、深圳市阿卡索资讯股份有限公司&#x000A;    - 479、青岛佳家康健康管理有限责任公司&#x000A;    - 480、蓝城兄弟&#x000A;    - 481、成都天府通金融服务股份有限公司&#x000A;    - 482、深圳云镖网络科技有限公司&#x000A;    - 483、上海影创科技&#x000A;    - 484、成都艾拉物联&#x000A;    - 485、北京客邻尚品网络技术有限公司&#x000A;    - 486、IT实战联盟&#x000A;    - 487、杭州尤拉夫科技有限公司&#x000A;    - 488、中大检测(湖南)股份有限公司&#x000A;    - 489、江苏电老虎工业互联网股份有限公司&#x000A;    - 490、上海助通信息科技有限公司&#x000A;    - 491、北京符节科技有限公司&#x000A;    - 492、杭州英祐科技有限公司&#x000A;    - 493、江苏电老虎工业互联网股份有限公司&#x000A;    - 494、深圳市点猫科技有限公司&#x000A;    - 495、杭州天音&#x000A;    - 496、深圳市二十一科技互联网有限公司&#x000A;    - 497、海南海口翎度科技&#x000A;    - 498、北京小趣智品科技有限公司&#x000A;    - 499、广州石竹计算机软件有限公司&#x000A;    - 500、深圳市惟客数据科技有限公司&#x000A;    - 501、中国医疗器械有限公司&#x000A;    - 502、上海云谦科技有限公司&#x000A;    - 503、上海磐农信息科技有限公司&#x000A;    - 504、广州领航食品有限公司&#x000A;    - 505、青岛掌讯通区块链科技有限公司&#x000A;    - 506、北京新网数码信息技术有限公司&#x000A;    - 507、超体信息科技(深圳)有限公司&#x000A;    - 508、长沙店帮手信息科技有限公司&#x000A;    - 509、上海助弓装饰工程有限公司&#x000A;    - 510、杭州寻联网络科技有限公司&#x000A;    - 511、成都大淘客科技有限公司&#x000A;    - 512、松果出行&#x000A;    - 513、深圳市唤梦科技有限公司&#x000A;    - 514、上汽集团商用车技术中心&#x000A;    - 515、北京中航讯科技股份有限公司&#x000A;    - 516、北龙中网(北京)科技有限责任公司&#x000A;    - 517、前海超级前台(深圳)信息技术有限公司&#x000A;    - 518、上海中商网络股份有限公司&#x000A;    - 519、上海助通信息科技有限公司&#x000A;    - 520、宁波聚臻智能科技有限公司&#x000A;    - 521、上海零动数码科技股份有限公司&#x000A;    - 522、浙江学海教育科技有限公司&#x000A;    - 523、聚学云(山东)信息技术有限公司&#x000A;    - 524、多氟多新材料股份有限公司&#x000A;    - 525、智慧眼科技股份有限公司&#x000A;    - 526、广东智通人才连锁股份有限公司&#x000A;    - 527、世纪开元智印互联科技集团股份有限公司&#x000A;    - 528、北京理想汽车【理想汽车】&#x000A;    - 529、巽逸科技(重庆)有限公司&#x000A;    - 530、义乌购电子商务有限公司&#x000A;    - 531、深圳市珂莱蒂尔服饰有限公司&#x000A;    - 532、江西国泰利民信息科技有限公司&#x000A;    - 533、广西广电大数据科技有限公司&#x000A;    - 534、杭州艾麦科技有限公司&#x000A;    - 535、广州小滴科技有限公司&#x000A;    - 536、佳缘科技股份有限公司&#x000A;    - 537、上海深擎信息科技有限公司&#x000A;    - 538、武商网&#x000A;    - 539、福建民本信息科技有限公司&#x000A;    - 540、杭州惠合信息科技有限公司&#x000A;    - 541、厦门爱立得科技有限公司&#x000A;    - 542、成都拟合未来科技有限公司&#x000A;    - 543、宁波聚臻智能科技有限公司&#x000A;    - 544、广东百慧科技有限公司&#x000A;    - 545、笨马网络&#x000A;    - 546、深圳市信安数字科技有限公司&#x000A;    - 547、深圳市思乐数据技术有限公司&#x000A;    - 548、四川绿源集科技有限公司&#x000A;    - 549、湖南云医链生物科技有限公司&#x000A;    - 550、杭州源诚科技有限公司&#x000A;    - 551、北京开课吧科技有限公司&#x000A;    - 552、北京多来点信息技术有限公司&#x000A;    - 553、JEECG BOOT低代码开发平台&#x000A;    - 554、苏州同元软控信息技术有限公司&#x000A;    - 555、江苏大泰信息技术有限公司&#x000A;    - 556、北京大禹汇智&#x000A;    - 557、北京盛哲科技有限公司&#x000A;    - ……&#x000A;&#x000A;&gt; 更多接入的公司，欢迎在 [登记地址](https://github.com/xuxueli/xxl-job/issues/1 ) 登记，登记仅仅为了产品推广。&#x000A;&#x000A;欢迎大家的关注和使用，XXL-JOB也将拥抱变化，持续发展。&#x000A;&#x000A;&#x000A;### 1.5 下载&#x000A;&#x000A;#### 文档地址&#x000A;&#x000A;- [中文文档](https://www.xuxueli.com/xxl-job/)&#x000A;- [English Documentation](https://www.xuxueli.com/xxl-job/en/)&#x000A;&#x000A;#### 源码仓库地址&#x000A;&#x000A;源码仓库地址 | Release Download&#x000A;--- | ---&#x000A;[https://github.com/xuxueli/xxl-job](https://github.com/xuxueli/xxl-job) | [Download](https://github.com/xuxueli/xxl-job/releases)  &#x000A;[http://gitee.com/xuxueli0323/xxl-job](http://gitee.com/xuxueli0323/xxl-job) | [Download](http://gitee.com/xuxueli0323/xxl-job/releases)&#x000A;&#x000A;&#x000A;#### 中央仓库地址&#x000A;&#x000A;```&#x000A;&lt;!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ --&gt;&#x000A;&lt;dependency&gt;&#x000A;    &lt;groupId&gt;com.xuxueli&lt;/groupId&gt;&#x000A;    &lt;artifactId&gt;xxl-job-core&lt;/artifactId&gt;&#x000A;    &lt;version&gt;${最新稳定版本}&lt;/version&gt;&#x000A;&lt;/dependency&gt;&#x000A;```&#x000A;&#x000A;&#x000A;### 1.6 环境&#x000A;- Maven3+&#x000A;- Jdk1.8+&#x000A;- Mysql5.7+&#x000A;&#x000A;&#x000A;## 二、快速入门&#x000A;&#x000A;### 2.1 初始化“调度数据库”&#x000A;请下载项目源码并解压，获取 &quot;调度数据库初始化SQL脚本&quot; 并执行即可。&#x000A;&#x000A;&quot;调度数据库初始化SQL脚本&quot; 位置为:&#x000A;&#x000A;    /xxl-job/doc/db/tables_xxl_job.sql&#x000A;&#x000A;调度中心支持集群部署，集群情况下各节点务必连接同一个mysql实例;&#x000A;&#x000A;如果mysql做主从,调度中心集群节点务必强制走主库;&#x000A;&#x000A;### 2.2 编译源码&#x000A;解压源码,按照maven格式将源码导入IDE, 使用maven进行编译即可，源码结构如下：&#x000A;&#x000A;    xxl-job-admin：调度中心&#x000A;    xxl-job-core：公共依赖&#x000A;    xxl-job-executor-samples：执行器Sample示例（选择合适的版本执行器，可直接使用，也可以参考其并将现有项目改造成执行器）&#x000A;        ：xxl-job-executor-sample-springboot：Springboot版本，通过Springboot管理执行器，推荐这种方式；&#x000A;        ：xxl-job-executor-sample-frameless：无框架版本；&#x000A;        &#x000A;&#x000A;### 2.3 配置部署“调度中心”&#x000A;&#x000A;    调度中心项目：xxl-job-admin&#x000A;    作用：统一管理任务调度平台上调度任务，负责触发调度执行，并且提供任务管理平台。&#x000A;&#x000A;#### 步骤一：调度中心配置：&#x000A;调度中心配置文件地址：&#x000A;&#x000A;    /xxl-job/xxl-job-admin/src/main/resources/application.properties&#x000A;&#x000A;&#x000A;调度中心配置内容说明：&#x000A;&#x000A;    ### 调度中心JDBC链接：链接地址请保持和 2.1章节 所创建的调度数据库的地址一致&#x000A;    spring.datasource.url=jdbc:mysql://127.0.0.1:3306/xxl_job?useUnicode=true&amp;characterEncoding=UTF-8&amp;autoReconnect=true&amp;serverTimezone=Asia/Shanghai&#x000A;    spring.datasource.username=root&#x000A;    spring.datasource.password=root_pwd&#x000A;    spring.datasource.driver-class-name=com.mysql.jdbc.Driver&#x000A;    &#x000A;    ### 报警邮箱&#x000A;    spring.mail.host=smtp.qq.com&#x000A;    spring.mail.port=25&#x000A;    spring.mail.username=xxx@qq.com&#x000A;    spring.mail.password=xxx&#x000A;    spring.mail.properties.mail.smtp.auth=true&#x000A;    spring.mail.properties.mail.smtp.starttls.enable=true&#x000A;    spring.mail.properties.mail.smtp.starttls.required=true&#x000A;    spring.mail.properties.mail.smtp.socketFactory.class=javax.net.ssl.SSLSocketFactory&#x000A;    &#x000A;    ### 调度中心通讯TOKEN [选填]：非空时启用；&#x000A;    xxl.job.accessToken=&#x000A;    &#x000A;    ### 调度中心国际化配置 [必填]： 默认为 &quot;zh_CN&quot;/中文简体, 可选范围为 &quot;zh_CN&quot;/中文简体, &quot;zh_TC&quot;/中文繁体 and &quot;en&quot;/英文；&#x000A;    xxl.job.i18n=zh_CN&#x000A;    &#x000A;    ## 调度线程池最大线程配置【必填】&#x000A;    xxl.job.triggerpool.fast.max=200&#x000A;    xxl.job.triggerpool.slow.max=100&#x000A;    &#x000A;    ### 调度中心日志表数据保存天数 [必填]：过期日志自动清理；限制大于等于7时生效，否则, 如-1，关闭自动清理功能；&#x000A;    xxl.job.logretentiondays=30&#x000A;    &#x000A;    &#x000A;&#x000A;#### 步骤二：部署项目：&#x000A;如果已经正确进行上述配置，可将项目编译打包部署。&#x000A;&#x000A;调度中心访问地址：http://localhost:8080/xxl-job-admin (该地址执行器将会使用到，作为回调地址)&#x000A;&#x000A;默认登录账号 &quot;admin/123456&quot;, 登录后运行界面如下图所示。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_6yC0.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;至此“调度中心”项目已经部署成功。&#x000A;&#x000A;#### 步骤三：调度中心集群（可选）：&#x000A;调度中心支持集群部署，提升调度系统容灾和可用性。&#x000A;&#x000A;调度中心集群部署时，几点要求和建议：&#x000A;- DB配置保持一致；&#x000A;- 集群机器时钟保持一致（单机集群忽视）；&#x000A;- 建议：推荐通过nginx为调度中心集群做负载均衡，分配域名。调度中心访问、执行器回调配置、调用API服务等操作均通过该域名进行。&#x000A;&#x000A;&#x000A;#### 其他：Docker 镜像方式搭建调度中心：&#x000A;&#x000A;- 下载镜像&#x000A;&#x000A;```&#x000A;// Docker地址：https://hub.docker.com/r/xuxueli/xxl-job-admin/     (建议指定版本号)&#x000A;docker pull xuxueli/xxl-job-admin&#x000A;```&#x000A;&#x000A;- 创建容器并运行&#x000A;&#x000A;```&#x000A;docker run -p 8080:8080 -v /tmp:/data/applogs --name xxl-job-admin  -d xuxueli/xxl-job-admin:{指定版本}&#x000A;&#x000A;/**&#x000A;* 如需自定义 mysql 等配置，可通过 &quot;-e PARAMS&quot; 指定，参数格式 PARAMS=&quot;--key=value  --key2=value2&quot; ；&#x000A;* 配置项参考文件：/xxl-job/xxl-job-admin/src/main/resources/application.properties&#x000A;* 如需自定义 JVM内存参数 等配置，可通过 &quot;-e JAVA_OPTS&quot; 指定，参数格式 JAVA_OPTS=&quot;-Xmx512m&quot; ；&#x000A;*/&#x000A;docker run -e PARAMS=&quot;--spring.datasource.url=jdbc:mysql://127.0.0.1:3306/xxl_job?useUnicode=true&amp;characterEncoding=UTF-8&amp;autoReconnect=true&amp;serverTimezone=Asia/Shanghai&quot; -p 8080:8080 -v /tmp:/data/applogs --name xxl-job-admin  -d xuxueli/xxl-job-admin:{指定版本}&#x000A;```&#x000A;&#x000A;&#x000A;### 2.4 配置部署“执行器项目”&#x000A;&#x000A;    “执行器”项目：xxl-job-executor-sample-springboot (提供多种版本执行器供选择，现以 springboot 版本为例，可直接使用，也可以参考其并将现有项目改造成执行器)&#x000A;    作用：负责接收“调度中心”的调度并执行；可直接部署执行器，也可以将执行器集成到现有业务项目中。&#x000A;    &#x000A;#### 步骤一：maven依赖&#x000A;确认pom文件中引入了 &quot;xxl-job-core&quot; 的maven依赖；&#x000A;    &#x000A;#### 步骤二：执行器配置&#x000A;执行器配置，配置文件地址：&#x000A;&#x000A;    /xxl-job/xxl-job-executor-samples/xxl-job-executor-sample-springboot/src/main/resources/application.properties&#x000A;&#x000A;执行器配置，配置内容说明：&#x000A;&#x000A;    ### 调度中心部署根地址 [选填]：如调度中心集群部署存在多个地址则用逗号分隔。执行器将会使用该地址进行&quot;执行器心跳注册&quot;和&quot;任务结果回调&quot;；为空则关闭自动注册；&#x000A;    xxl.job.admin.addresses=http://127.0.0.1:8080/xxl-job-admin&#x000A;    &#x000A;    ### 执行器通讯TOKEN [选填]：非空时启用；&#x000A;    xxl.job.accessToken=&#x000A;    &#x000A;    ### 执行器AppName [选填]：执行器心跳注册分组依据；为空则关闭自动注册&#x000A;    xxl.job.executor.appname=xxl-job-executor-sample&#x000A;    ### 执行器注册 [选填]：优先使用该配置作为注册地址，为空时使用内嵌服务 ”IP:PORT“ 作为注册地址。从而更灵活的支持容器类型执行器动态IP和动态映射端口问题。&#x000A;    xxl.job.executor.address=&#x000A;    ### 执行器IP [选填]：默认为空表示自动获取IP，多网卡时可手动设置指定IP，该IP不会绑定Host仅作为通讯实用；地址信息用于 &quot;执行器注册&quot; 和 &quot;调度中心请求并触发任务&quot;；&#x000A;    xxl.job.executor.ip=&#x000A;    ### 执行器端口号 [选填]：小于等于0则自动获取；默认端口为9999，单机部署多个执行器时，注意要配置不同执行器端口；&#x000A;    xxl.job.executor.port=9999&#x000A;    ### 执行器运行日志文件存储磁盘路径 [选填] ：需要对该路径拥有读写权限；为空则使用默认路径；&#x000A;    xxl.job.executor.logpath=/data/applogs/xxl-job/jobhandler&#x000A;    ### 执行器日志文件保存天数 [选填] ： 过期日志自动清理, 限制值大于等于3时生效; 否则, 如-1, 关闭自动清理功能；&#x000A;    xxl.job.executor.logretentiondays=30&#x000A;    &#x000A;&#x000A;#### 步骤三：执行器组件配置&#x000A;&#x000A;执行器组件，配置文件地址：&#x000A;&#x000A;    /xxl-job/xxl-job-executor-samples/xxl-job-executor-sample-springboot/src/main/java/com/xxl/job/executor/core/config/XxlJobConfig.java&#x000A;&#x000A;执行器组件，配置内容说明：&#x000A;&#x000A;```&#x000A;@Bean&#x000A;public XxlJobSpringExecutor xxlJobExecutor() {&#x000A;    logger.info(&quot;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt; xxl-job config init.&quot;);&#x000A;    XxlJobSpringExecutor xxlJobSpringExecutor = new XxlJobSpringExecutor();&#x000A;    xxlJobSpringExecutor.setAdminAddresses(adminAddresses);&#x000A;    xxlJobSpringExecutor.setAppname(appname);&#x000A;    xxlJobSpringExecutor.setIp(ip);&#x000A;    xxlJobSpringExecutor.setPort(port);&#x000A;    xxlJobSpringExecutor.setAccessToken(accessToken);&#x000A;    xxlJobSpringExecutor.setLogPath(logPath);&#x000A;    xxlJobSpringExecutor.setLogRetentionDays(logRetentionDays);&#x000A;&#x000A;    return xxlJobSpringExecutor;&#x000A;}&#x000A;```&#x000A;&#x000A;#### 步骤四：部署执行器项目：&#x000A;如果已经正确进行上述配置，可将执行器项目编译打部署，系统提供多种执行器Sample示例项目，选择其中一个即可，各自的部署方式如下。&#x000A;&#x000A;    xxl-job-executor-sample-springboot：项目编译打包成springboot类型的可执行JAR包，命令启动即可；&#x000A;    xxl-job-executor-sample-frameless：项目编译打包成JAR包，命令启动即可；&#x000A;    &#x000A;&#x000A;至此“执行器”项目已经部署结束。&#x000A;&#x000A;#### 步骤五：执行器集群（可选）：&#x000A;执行器支持集群部署，提升调度系统可用性，同时提升任务处理能力。&#x000A;&#x000A;执行器集群部署时，几点要求和建议：&#x000A;- 执行器回调地址（xxl.job.admin.addresses）需要保持一致；执行器根据该配置进行执行器自动注册等操作。 &#x000A;- 同一个执行器集群内AppName（xxl.job.executor.appname）需要保持一致；调度中心根据该配置动态发现不同集群的在线执行器列表。&#x000A;&#x000A;&#x000A;### 2.5 开发第一个任务“Hello World”       &#x000A;本示例以新建一个 “GLUE模式(Java)” 运行模式的任务为例。更多有关任务的详细配置，请查看“章节三：任务详解”。&#x000A;（ “GLUE模式(Java)”的执行代码托管到调度中心在线维护，相比“Bean模式任务”需要在执行器项目开发部署上线，更加简便轻量）&#x000A;&#x000A;&gt; 前提：请确认“调度中心”和“执行器”项目已经成功部署并启动；&#x000A;&#x000A;#### 步骤一：新建任务：&#x000A;登录调度中心，点击下图所示“新建任务”按钮，新建示例任务。然后，参考下面截图中任务的参数配置，点击保存。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_o8HQ.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAsz.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;&#x000A;#### 步骤二：“GLUE模式(Java)” 任务开发：&#x000A;请点击任务右侧 “GLUE” 按钮，进入 “GLUE编辑器开发界面” ，见下图。“GLUE模式(Java)” 运行模式的任务默认已经初始化了示例任务代码，即打印Hello World。&#x000A;（ “GLUE模式(Java)” 运行模式的任务实际上是一段继承自IJobHandler的Java类代码，它在执行器项目中运行，可使用@Resource/@Autowire注入执行器里中的其他服务，详细介绍请查看第三章节）&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Fgql.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_dNUJ.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;#### 步骤三：触发执行：&#x000A;请点击任务右侧 “执行” 按钮，可手动触发一次任务执行（通常情况下，通过配置Cron表达式进行任务调度触发）。&#x000A;&#x000A;#### 步骤四：查看日志： &#x000A;请点击任务右侧 “日志” 按钮，可前往任务日志界面查看任务日志。&#x000A;在任务日志界面中，可查看该任务的历史调度记录以及每一次调度的任务调度信息、执行参数和执行信息。运行中的任务点击右侧的“执行日志”按钮，可进入日志控制台查看实时执行日志。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_inc8.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;在日志控制台，可以Rolling方式实时查看任务在执行器一侧运行输出的日志信息，实时监控任务进度；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_eYrv.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;## 三、任务详解&#x000A;&#x000A;### 配置属性详细说明：&#x000A;&#x000A;    基础配置：&#x000A;        - 执行器：任务的绑定的执行器，任务触发调度时将会自动发现注册成功的执行器, 实现任务自动发现功能; 另一方面也可以方便的进行任务分组。每个任务必须绑定一个执行器, 可在 &quot;执行器管理&quot; 进行设置;&#x000A;        - 任务描述：任务的描述信息，便于任务管理；&#x000A;        - 负责人：任务的负责人；&#x000A;        - 报警邮件：任务调度失败时邮件通知的邮箱地址，支持配置多邮箱地址，配置多个邮箱地址时用逗号分隔；&#x000A;        &#x000A;    触发配置：&#x000A;        - 调度类型：&#x000A;            无：该类型不会主动触发调度；&#x000A;            CRON：该类型将会通过CRON，触发任务调度；&#x000A;            固定速度：该类型将会以固定速度，触发任务调度；按照固定的间隔时间，周期性触发；&#x000A;            固定延迟：该类型将会以固定延迟，触发任务调度；按照固定的延迟时间，从上次调度结束后开始计算延迟时间，到达延迟时间后触发下次调度；&#x000A;        - CRON：触发任务执行的Cron表达式；&#x000A;        - 固定速度：固件速度的时间间隔，单位为秒；&#x000A;        - 固定延迟：固件延迟的时间间隔，单位为秒；&#x000A;        &#x000A;    任务配置：&#x000A;        - 运行模式：&#x000A;            BEAN模式：任务以JobHandler方式维护在执行器端；需要结合 &quot;JobHandler&quot; 属性匹配执行器中任务；&#x000A;            GLUE模式(Java)：任务以源码方式维护在调度中心；该模式的任务实际上是一段继承自IJobHandler的Java类代码并 &quot;groovy&quot; 源码方式维护，它在执行器项目中运行，可使用@Resource/@Autowire注入执行器里中的其他服务；&#x000A;            GLUE模式(Shell)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 &quot;shell&quot; 脚本；&#x000A;            GLUE模式(Python)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 &quot;python&quot; 脚本；&#x000A;            GLUE模式(PHP)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 &quot;php&quot; 脚本；&#x000A;            GLUE模式(NodeJS)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 &quot;nodejs&quot; 脚本；&#x000A;            GLUE模式(PowerShell)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 &quot;PowerShell&quot; 脚本；&#x000A;        - JobHandler：运行模式为 &quot;BEAN模式&quot; 时生效，对应执行器中新开发的JobHandler类“@JobHandler”注解自定义的value值；&#x000A;        - 执行参数：任务执行所需的参数；     &#x000A;        &#x000A;    高级配置：&#x000A;        - 路由策略：当执行器集群部署时，提供丰富的路由策略，包括；&#x000A;            FIRST（第一个）：固定选择第一个机器；&#x000A;            LAST（最后一个）：固定选择最后一个机器；&#x000A;            ROUND（轮询）：；&#x000A;            RANDOM（随机）：随机选择在线的机器；&#x000A;            CONSISTENT_HASH（一致性HASH）：每个任务按照Hash算法固定选择某一台机器，且所有任务均匀散列在不同机器上。&#x000A;            LEAST_FREQUENTLY_USED（最不经常使用）：使用频率最低的机器优先被选举；&#x000A;            LEAST_RECENTLY_USED（最近最久未使用）：最久未使用的机器优先被选举；&#x000A;            FAILOVER（故障转移）：按照顺序依次进行心跳检测，第一个心跳检测成功的机器选定为目标执行器并发起调度；&#x000A;            BUSYOVER（忙碌转移）：按照顺序依次进行空闲检测，第一个空闲检测成功的机器选定为目标执行器并发起调度；&#x000A;            SHARDING_BROADCAST(分片广播)：广播触发对应集群中所有机器执行一次任务，同时系统自动传递分片参数；可根据分片参数开发分片任务；&#x000A;        - 子任务：每个任务都拥有一个唯一的任务ID(任务ID可以从任务列表获取)，当本任务执行结束并且执行成功时，将会触发子任务ID所对应的任务的一次主动调度。&#x000A;        - 调度过期策略：&#x000A;            - 忽略：调度过期后，忽略过期的任务，从当前时间开始重新计算下次触发时间；&#x000A;            - 立即执行一次：调度过期后，立即执行一次，并从当前时间开始重新计算下次触发时间；&#x000A;        - 阻塞处理策略：调度过于密集执行器来不及处理时的处理策略；&#x000A;            单机串行（默认）：调度请求进入单机执行器后，调度请求进入FIFO队列并以串行方式运行；&#x000A;            丢弃后续调度：调度请求进入单机执行器后，发现执行器存在运行的调度任务，本次请求将会被丢弃并标记为失败；&#x000A;            覆盖之前调度：调度请求进入单机执行器后，发现执行器存在运行的调度任务，将会终止运行中的调度任务并清空队列，然后运行本地调度任务；&#x000A;        - 任务超时时间：支持自定义任务超时时间，任务运行超时将会主动中断任务；&#x000A;        - 失败重试次数；支持自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；&#x000A;    &#x000A;    &#x000A;    &#x000A;&#x000A;    &#x000A;### 3.1 BEAN模式（类形式）&#x000A;&#x000A;Bean模式任务，支持基于类的开发方式，每个任务对应一个Java类。&#x000A;&#x000A;- 优点：不限制项目环境，兼容性好。即使是无框架项目，如main方法直接启动的项目也可以提供支持，可以参考示例项目 &quot;xxl-job-executor-sample-frameless&quot;；&#x000A;- 缺点：&#x000A;    - 每个任务需要占用一个Java类，造成类的浪费；&#x000A;    - 不支持自动扫描任务并注入到执行器容器，需要手动注入。&#x000A;&#x000A;#### 步骤一：执行器项目中，开发Job类：&#x000A;&#x000A;    1、开发一个继承自&quot;com.xxl.job.core.handler.IJobHandler&quot;的JobHandler类，实现其中任务方法。&#x000A;    2、手动通过如下方式注入到执行器容器。&#x000A;    ```&#x000A;    XxlJobExecutor.registJobHandler(&quot;demoJobHandler&quot;, new DemoJobHandler());&#x000A;    ```&#x000A;&#x000A;#### 步骤二：调度中心，新建调度任务&#x000A;后续步骤和 &quot;3.2 BEAN模式（方法形式）&quot;一致，可以前往参考。&#x000A;&#x000A;&#x000A;### 3.2 BEAN模式（方法形式）&#x000A;&#x000A;Bean模式任务，支持基于方法的开发方式，每个任务对应一个方法。&#x000A;&#x000A;- 优点：&#x000A;    - 每个任务只需要开发一个方法，并添加&quot;@XxlJob&quot;注解即可，更加方便、快速。&#x000A;    - 支持自动扫描任务并注入到执行器容器。&#x000A;- 缺点：要求Spring容器环境；&#x000A;&#x000A;&gt;基于方法开发的任务，底层会生成JobHandler代理，和基于类的方式一样，任务也会以JobHandler的形式存在于执行器任务容器中。&#x000A;&#x000A;#### 步骤一：执行器项目中，开发Job方法：&#x000A;&#x000A;    1、任务开发：在Spring Bean实例中，开发Job方法；&#x000A;    2、注解配置：为Job方法添加注解 &quot;@XxlJob(value=&quot;自定义jobhandler名称&quot;, init = &quot;JobHandler初始化方法&quot;, destroy = &quot;JobHandler销毁方法&quot;)&quot;，注解value值对应的是调度中心新建任务的JobHandler属性的值。&#x000A;    3、执行日志：需要通过 &quot;XxlJobHelper.log&quot; 打印执行日志；&#x000A;    4、任务结果：默认任务结果为 &quot;成功&quot; 状态，不需要主动设置；如有诉求，比如设置任务结果为失败，可以通过 &quot;XxlJobHelper.handleFail/handleSuccess&quot; 自主设置任务结果；&#x000A;    &#x000A;```&#x000A;// 可参考Sample示例执行器中的 &quot;com.xxl.job.executor.service.jobhandler.SampleXxlJob&quot; ，如下：&#x000A;@XxlJob(&quot;demoJobHandler&quot;)&#x000A;public void demoJobHandler() throws Exception {&#x000A;    XxlJobHelper.log(&quot;XXL-JOB, Hello World.&quot;);&#x000A;}&#x000A;```&#x000A;&#x000A;#### 步骤二：调度中心，新建调度任务&#x000A;参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 &quot;BEAN模式&quot;，JobHandler属性填写任务注解“@XxlJob”中定义的值；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAsz.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;#### 原生内置Bean模式任务&#x000A;为方便用户参考与快速实用，示例执行器内原生提供多个Bean模式任务Handler，可以直接配置实用，如下：&#x000A;&#x000A;- demoJobHandler：简单示例任务，任务内部模拟耗时任务逻辑，用户可在线体验Rolling Log等功能；&#x000A;- shardingJobHandler：分片示例任务，任务内部模拟处理分片参数，可参考熟悉分片任务；&#x000A;- httpJobHandler：通用HTTP任务Handler；业务方只需要提供HTTP链接等信息即可，不限制语言、平台。示例任务入参如下：&#x000A;    ```&#x000A;    url: http://www.xxx.com&#x000A;    method: get 或 post&#x000A;    data: post-data&#x000A;    ```&#x000A;- commandJobHandler：通用命令行任务Handler；业务方只需要提供命令行即可；如 “pwd”命令；&#x000A;&#x000A;&#x000A;### 3.3 GLUE模式(Java)&#x000A;任务以源码方式维护在调度中心，支持通过Web IDE在线更新，实时编译和生效，因此不需要指定JobHandler。开发流程如下：&#x000A;&#x000A;#### 步骤一：调度中心，新建调度任务：&#x000A;参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 &quot;GLUE模式(Java)&quot;；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_tJOq.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;#### 步骤二：开发任务代码：&#x000A;选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。&#x000A;&#x000A;版本回溯功能（支持30个版本的版本回溯）：在GLUE任务的Web IDE界面，选择右上角下拉框“版本回溯”，会列出该GLUE的更新历史，选择相应版本即可显示该版本代码，保存后GLUE代码即回退到对应的历史版本；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_dNUJ.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 3.4 GLUE模式(Shell)&#x000A;&#x000A;#### 步骤一：调度中心，新建调度任务   &#x000A;参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 &quot;GLUE模式(Shell)&quot;；&#x000A;&#x000A;#### 步骤二：开发任务代码：&#x000A;选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。&#x000A;&#x000A;该模式的任务实际上是一段 &quot;shell&quot; 脚本；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_iUw0.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 3.4 GLUE模式(Python)&#x000A;&#x000A;#### 步骤一：调度中心，新建调度任务   &#x000A;参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 &quot;GLUE模式(Python)&quot;；&#x000A;&#x000A;#### 步骤二：开发任务代码：&#x000A;选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。&#x000A;&#x000A;该模式的任务实际上是一段 &quot;python&quot; 脚本；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_BPLG.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 3.5 GLUE模式(NodeJS)&#x000A;&#x000A;#### 步骤一：调度中心，新建调度任务   &#x000A;参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 &quot;GLUE模式(NodeJS)&quot;；&#x000A;&#x000A;#### 步骤二：开发任务代码：&#x000A;选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。&#x000A;&#x000A;该模式的任务实际上是一段 &quot;nodeJS&quot; 脚本；&#x000A;&#x000A;### 3.6 GLUE模式(PHP)&#x000A;同上&#x000A;&#x000A;### 3.7 GLUE模式(PowerShell)&#x000A;同上&#x000A;&#x000A;&#x000A;&#x000A;## 四、操作指南&#x000A;&#x000A;### 4.1 配置执行器&#x000A;点击进入&quot;执行器管理&quot;界面, 如下图:&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Hr2T.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;    1、&quot;调度中心OnLine:&quot;右侧显示在线的&quot;调度中心&quot;列表, 任务执行结束后, 将会以failover的模式进行回调调度中心通知执行结果, 避免回调的单点风险;&#x000A;    2、&quot;执行器列表&quot; 中显示在线的执行器列表, 可通过&quot;OnLine 机器&quot;查看对应执行器的集群机器。&#x000A;&#x000A;点击按钮 &quot;+新增执行器&quot; 弹框如下图, 可新增执行器配置:&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_V3vF.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;执行器属性说明&#x000A;&#x000A;    AppName: 是每个执行器集群的唯一标示AppName, 执行器会周期性以AppName为对象进行自动注册。可通过该配置自动发现注册成功的执行器, 供任务调度时使用;&#x000A;    名称: 执行器的名称, 因为AppName限制字母数字等组成,可读性不强, 名称为了提高执行器的可读性;&#x000A;    排序: 执行器的排序, 系统中需要执行器的地方,如任务新增, 将会按照该排序读取可用的执行器列表;&#x000A;    注册方式：调度中心获取执行器地址的方式；&#x000A;        自动注册：执行器自动进行执行器注册，调度中心通过底层注册表可以动态发现执行器机器地址；&#x000A;        手动录入：人工手动录入执行器的地址信息，多地址逗号分隔，供调度中心使用；&#x000A;    机器地址：&quot;注册方式&quot;为&quot;手动录入&quot;时有效，支持人工维护执行器的地址信息；&#x000A;&#x000A;### 4.2 新建任务&#x000A;进入任务管理界面，点击“新增任务”按钮，在弹出的“新增任务”界面配置任务属性后保存即可。详情页参考章节 &quot;三、任务详解&quot;。&#x000A;&#x000A;### 4.3 编辑任务&#x000A;进入任务管理界面，选中指定任务。点击该任务右侧“编辑”按钮，在弹出的“编辑任务”界面更新任务属性后保存即可，可以修改设置的任务属性信息：&#x000A;&#x000A;### 4.4 编辑GLUE代码&#x000A;&#x000A;该操作仅针对GLUE任务。&#x000A;&#x000A;选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发。可参考章节 &quot;3.3 GLUE模式(Java)&quot;。&#x000A;&#x000A;### 4.5 启动/停止任务&#x000A;可对任务进行“启动”和“停止”操作。&#x000A;需要注意的是，此处的启动/停止仅针对任务的后续调度触发行为，不会影响到已经触发的调度任务，如需终止已经触发的调度任务，可查看“4.9 终止运行中的任务”&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 4.6 手动触发一次调度&#x000A;点击“执行”按钮，可手动触发一次任务调度，不影响原有调度规则。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 4.7 查看调度日志&#x000A;点击“日志”按钮，可以查看任务历史调度日志。在历史调入日志界面可查看每次任务调度的调度结果、执行结果等，点击“执行日志”按钮可查看执行器完整日志。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_UDSo.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;    调度时间：&quot;调度中心&quot;触发本次调度并向&quot;执行器&quot;发送任务执行信号的时间；&#x000A;    调度结果：&quot;调度中心&quot;触发本次调度的结果，200表示成功，500或其他表示失败；&#x000A;    调度备注：&quot;调度中心&quot;触发本次调度的日志信息；&#x000A;    执行器地址：本次任务执行的机器地址&#x000A;    运行模式：触发调度时任务的运行模式，运行模式可参考章节 &quot;三、任务详解&quot;；&#x000A;    任务参数：本地任务执行的入参&#x000A;    执行时间：&quot;执行器&quot;中本次任务执行结束后回调的时间；&#x000A;    执行结果：&quot;执行器&quot;中本次任务执行的结果，200表示成功，500或其他表示失败；&#x000A;    执行备注：&quot;执行器&quot;中本次任务执行的日志信息；&#x000A;    操作：&#x000A;        &quot;执行日志&quot;按钮：点击可查看本地任务执行的详细日志信息；详见“4.8 查看执行日志”；&#x000A;        &quot;终止任务&quot;按钮：点击可终止本地调度对应执行器上本任务的执行线程，包括未执行的阻塞任务一并被终止；&#x000A;&#x000A;### 4.8 查看执行日志&#x000A;点击执行日志右侧的 “执行日志” 按钮，可跳转至执行日志界面，可以查看业务代码中打印的完整日志，如下图；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_tvGI.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 4.9 终止运行中的任务&#x000A;仅针对执行中的任务。&#x000A;在任务日志界面，点击右侧的“终止任务”按钮，将会向本次任务对应的执行器发送任务终止请求，将会终止掉本次任务，同时会清空掉整个任务执行队列。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_hIci.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;任务终止时通过 &quot;interrupt&quot; 执行线程的方式实现, 将会触发 &quot;InterruptedException&quot; 异常。因此如果JobHandler内部catch到了该异常并消化掉的话, 任务终止功能将不可用。&#x000A;&#x000A;因此, 如果遇到上述任务终止不可用的情况, 需要在JobHandler中应该针对 &quot;InterruptedException&quot; 异常进行特殊处理 (向上抛出) , 正确逻辑如下:&#x000A;```&#x000A;try{&#x000A;    // do something&#x000A;} catch (Exception e) {&#x000A;    if (e instanceof InterruptedException) {&#x000A;        throw e;&#x000A;    }&#x000A;    logger.warn(&quot;{}&quot;, e);&#x000A;}&#x000A;```&#x000A;&#x000A;而且，在JobHandler中开启子线程时，子线程也不可catch处理&quot;InterruptedException&quot;，应该主动向上抛出。&#x000A;&#x000A;任务终止时会执行对应JobHandler的&quot;destroy()&quot;方法，可以借助该方法处理一些资源回收的逻辑。&#x000A;&#x000A;&#x000A;### 4.10 删除执行日志&#x000A;在任务日志界面，选中执行器和任务之后，点击右侧的&quot;删除&quot;按钮将会出现&quot;日志清理&quot;弹框，弹框中支持选择不同类型的日志清理策略，选中后点击&quot;确定&quot;按钮即可进行日志清理操作；&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Ypik.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_EB65.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 4.11 删除任务&#x000A;点击删除按钮，可以删除对应任务。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Z9Qr.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 4.12 用户管理&#x000A;进入 &quot;用户管理&quot; 界面，可查看和管理用户信息；&#x000A;&#x000A;目前用户分为两种角色：&#x000A;- 管理员：拥有全量权限，支持在线管理用户信息，为用户分配权限，权限分配粒度为执行器；&#x000A;- 普通用户：仅拥有被分配权限的执行器，及相关任务的操作权限；&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_1001.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_1002.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;&#x000A;## 五、总体设计&#x000A;### 5.1 源码目录介绍&#x000A;    - /doc :文档资料&#x000A;    - /db :“调度数据库”建表脚本&#x000A;    - /xxl-job-admin :调度中心，项目源码&#x000A;    - /xxl-job-core :公共Jar依赖&#x000A;    - /xxl-job-executor-samples :执行器，Sample示例项目（大家可以在该项目上进行开发，也可以将现有项目改造生成执行器项目）&#x000A;&#x000A;### 5.2 “调度数据库”配置&#x000A;XXL-JOB调度模块基于自研调度组件并支持集群部署，调度数据库表说明如下：&#x000A;&#x000A;    - xxl_job_lock：任务调度锁表；&#x000A;    - xxl_job_group：执行器信息表，维护任务执行器信息；&#x000A;    - xxl_job_info：调度扩展信息表： 用于保存XXL-JOB调度任务的扩展信息，如任务分组、任务名、机器地址、执行器、执行入参和报警邮件等等；&#x000A;    - xxl_job_log：调度日志表： 用于保存XXL-JOB任务调度的历史信息，如调度结果、执行结果、调度入参、调度机器和执行器等等；&#x000A;    - xxl_job_log_report：调度日志报表：用户存储XXL-JOB任务调度日志的报表，调度中心报表功能页面会用到；&#x000A;    - xxl_job_logglue：任务GLUE日志：用于保存GLUE更新历史，用于支持GLUE的版本回溯功能；&#x000A;    - xxl_job_registry：执行器注册表，维护在线的执行器和调度中心机器地址信息；&#x000A;    - xxl_job_user：系统用户表；&#x000A;&#x000A;&#x000A;### 5.3 架构设计&#x000A;#### 5.3.1 设计思想&#x000A;将调度行为抽象形成“调度中心”公共平台，而平台自身并不承担业务逻辑，“调度中心”负责发起调度请求。&#x000A;&#x000A;将任务抽象成分散的JobHandler，交由“执行器”统一管理，“执行器”负责接收调度请求并执行对应的JobHandler中业务逻辑。&#x000A;&#x000A;因此，“调度”和“任务”两部分可以相互解耦，提高系统整体稳定性和扩展性；&#x000A;&#x000A;#### 5.3.2 系统组成&#x000A;- **调度模块（调度中心）**：&#x000A;    负责管理调度信息，按照调度配置发出调度请求，自身不承担业务代码。调度系统与任务解耦，提高了系统可用性和稳定性，同时调度系统性能不再受限于任务模块；&#x000A;    支持可视化、简单且动态的管理调度信息，包括任务新建，更新，删除，GLUE开发和任务报警等，所有上述操作都会实时生效，同时支持监控调度结果以及执行日志，支持执行器Failover。&#x000A;- **执行模块（执行器）**：&#x000A;    负责接收调度请求并执行任务逻辑。任务模块专注于任务的执行等操作，开发和维护更加简单和高效；&#x000A;    接收“调度中心”的执行请求、终止请求和日志请求等。&#x000A;&#x000A;#### 5.3.3 架构图&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Qohm.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;### 5.4 调度模块剖析&#x000A;#### 5.4.1 quartz的不足&#x000A;Quartz作为开源作业调度中的佼佼者，是作业调度的首选。但是集群环境中Quartz采用API的方式对任务进行管理，从而可以避免上述问题，但是同样存在以下问题：&#x000A;   &#x000A;- 问题一：调用API的的方式操作任务，不人性化；&#x000A;- 问题二：需要持久化业务QuartzJobBean到底层数据表中，系统侵入性相当严重。&#x000A;- 问题三：调度逻辑和QuartzJobBean耦合在同一个项目中，这将导致一个问题，在调度任务数量逐渐增多，同时调度任务逻辑逐渐加重的情况下，此时调度系统的性能将大大受限于业务；&#x000A;- 问题四：quartz底层以“抢占式”获取DB锁并由抢占成功节点负责运行任务，会导致节点负载悬殊非常大；而XXL-JOB通过执行器实现“协同分配式”运行任务，充分发挥集群优势，负载各节点均衡。&#x000A;&#x000A;XXL-JOB弥补了quartz的上述不足之处。&#x000A;&#x000A;#### 5.4.2 自研调度模块&#x000A;XXL-JOB最终选择自研调度组件（早期调度组件基于Quartz）；一方面是为了精简系统降低冗余依赖，另一方面是为了提供系统的可控度与稳定性；&#x000A;&#x000A;XXL-JOB中“调度模块”和“任务模块”完全解耦，调度模块进行任务调度时，将会解析不同的任务参数发起远程调用，调用各自的远程执行器服务。这种调用模型类似RPC调用，调度中心提供调用代理的功能，而执行器提供远程服务的功能。&#x000A;&#x000A;#### 5.4.3 调度中心HA（集群）&#x000A;基于数据库的集群方案，数据库选用Mysql；集群分布式并发环境中进行定时任务调度时，会在各个节点会上报任务，存到数据库中，执行时会从数据库中取出触发器来执行，如果触发器的名称和执行时间相同，则只有一个节点去执行此任务。&#x000A;&#x000A;#### 5.4.4 调度线程池&#x000A;调度采用线程池方式实现，避免单线程因阻塞而引起任务调度延迟。&#x000A;&#x000A;#### 5.4.5 并行调度&#x000A;XXL-JOB调度模块默认采用并行机制，在多线程调度的情况下，调度模块被阻塞的几率很低，大大提高了调度系统的承载量。&#x000A;&#x000A;XXL-JOB的不同任务之间并行调度、并行执行。&#x000A;XXL-JOB的单个任务，针对多个执行器是并行运行的，针对单个执行器是串行执行的。同时支持任务终止。&#x000A;&#x000A;#### 5.4.6 过期处理策略&#x000A;任务调度错过触发时间时的处理策略：&#x000A;- 可能原因：服务重启；调度线程被阻塞，线程被耗尽；上次调度持续阻塞，下次调度被错过；&#x000A;- 处理策略：&#x000A;    - 过期超5s：本次忽略，当前时间开始计算下次触发时间&#x000A;    - 过期5s内：立即触发一次，当前时间开始计算下次触发时间&#x000A;&#x000A;&#x000A;#### 5.4.7 日志回调服务&#x000A;调度模块的“调度中心”作为Web服务部署时，一方面承担调度中心功能，另一方面也为执行器提供API服务。&#x000A;&#x000A;调度中心提供的&quot;日志回调服务API服务&quot;代码位置如下：&#x000A;```&#x000A;xxl-job-admin#com.xxl.job.admin.controller.JobApiController.callback&#x000A;```&#x000A;&#x000A;“执行器”在接收到任务执行请求后，执行任务，在执行结束之后会将执行结果回调通知“调度中心”：&#x000A;&#x000A;#### 5.4.8 任务HA（Failover）&#x000A;执行器如若集群部署，调度中心将会感知到在线的所有执行器，如“127.0.0.1:9997, 127.0.0.1:9998, 127.0.0.1:9999”。&#x000A;&#x000A;当任务&quot;路由策略&quot;选择&quot;故障转移(FAILOVER)&quot;时，当调度中心每次发起调度请求时，会按照顺序对执行器发出心跳检测请求，第一个检测为存活状态的执行器将会被选定并发送调度请求。&#x000A;&#x000A;调度成功后，可在日志监控界面查看“调度备注”，如下；&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_jrdI.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;“调度备注”可以看出本地调度运行轨迹，执行器的&quot;注册方式&quot;、&quot;地址列表&quot;和任务的&quot;路由策略&quot;。&quot;故障转移(FAILOVER)&quot;路由策略下，调度中心首先对第一个地址进行心跳检测，心跳失败因此自动跳过，第二个依然心跳检测失败……&#x000A;直至心跳检测第三个地址“127.0.0.1:9999”成功，选定为“目标执行器”；然后对“目标执行器”发送调度请求，调度流程结束，等待执行器回调执行结果。&#x000A;&#x000A;#### 5.4.9 调度日志&#x000A;调度中心每次进行任务调度，都会记录一条任务日志，任务日志主要包括以下三部分内容：&#x000A;&#x000A;- 任务信息：包括“执行器地址”、“JobHandler”和“执行参数”等属性，点击任务ID按钮可查看，根据这些参数，可以精确的定位任务执行的具体机器和任务代码；&#x000A;- 调度信息：包括“调度时间”、“调度结果”和“调度日志”等，根据这些参数，可以了解“调度中心”发起调度请求时具体情况。&#x000A;- 执行信息：包括“执行时间”、“执行结果”和“执行日志”等，根据这些参数，可以了解在“执行器”端任务执行的具体情况；&#x000A;&#x000A;调度日志，针对单次调度，属性说明如下：&#x000A;- 执行器地址：任务执行的机器地址；&#x000A;- JobHandler：Bean模式表示任务执行的JobHandler名称；&#x000A;- 任务参数：任务执行的入参；&#x000A;- 调度时间：调度中心，发起调度的时间；&#x000A;- 调度结果：调度中心，发起调度的结果，SUCCESS或FAIL；&#x000A;- 调度备注：调度中心，发起调度的备注信息，如地址心跳检测日志等；&#x000A;- 执行时间：执行器，任务执行结束后回调的时间；&#x000A;- 执行结果：执行器，任务执行的结果，SUCCESS或FAIL；&#x000A;- 执行备注：执行器，任务执行的备注信息，如异常日志等；&#x000A;- 执行日志：任务执行过程中，业务代码中打印的完整执行日志，见“4.8 查看执行日志”；&#x000A;&#x000A;#### 5.4.10 任务依赖&#x000A;原理：XXL-JOB中每个任务都对应有一个任务ID，同时，每个任务支持设置属性“子任务ID”，因此，通过“任务ID”可以匹配任务依赖关系。&#x000A;&#x000A;当父任务执行结束并且执行成功时，将会根据“子任务ID”匹配子任务依赖，如果匹配到子任务，将会主动触发一次子任务的执行。&#x000A;&#x000A;在任务日志界面，点击任务的“执行备注”的“查看”按钮，可以看到匹配子任务以及触发子任务执行的日志信息，如无信息则表示未触发子任务执行，可参考下图。&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_Wb2o.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;![输入图片说明](https://www.xuxueli.com/doc/static/xxl-job/images/img_jOAU.png &quot;在这里输入图片标题&quot;)&#x000A;&#x000A;#### 5.4.11  全异步化 &amp; 轻量级&#x000A;&#x000A;- 全异步化设计：XXL-JOB系统中业务逻辑在远程执行器执行，触发流程全异步化设计。相比直接在调度中心内部执行业务逻辑，极大的降低了调度线程占用时间；&#x000A;    - 异步调度：调度中心每次任务触发时仅发送一次调度请求，该调度请求首先推送“异步调度队列”，然后异步推送给远程执行器&#x000A;    - 异步执行：执行器会将请求存入“异步执行队列”并且立即响应调度中心，异步运行。&#x000A;- 轻量级设计：XXL-JOB调度中心中每个JOB逻辑非常 “轻”，在全异步化的基础上，单个JOB一次运行平均耗时基本在 &quot;10ms&quot; 之内（基本为一次请求的网络开销）；因此，可以保证使用有限的线程支撑大量的JOB并发运行；&#x000A;&#x000A;得益于上述两点优化，理论上默认配置下的调度中心，单机能够支撑 5000 任务并发运行稳定运行；&#x000A;&#x000A;实际场景中，由于调度中心与执行器网络ping延迟不同、DB读写耗时不同、任务调度密集程度不同，会导致任务量上限会上下波动。&#x000A;&#x000A;如若需要支撑更多的任务量，可以通过 &quot;调大调度线程数&quot; 、&quot;降低调度中心与执行器ping延迟&quot; 和 &quot;提升机器配置&quot; 几种方式优化。&#x000A;&#x000A;#### 5.4.12 均衡调度    &#x000A;调度中心在集群部署时会自动进行任务平均分配，触发组件每次获取与线程池数量（调度中心支持自定义调度线程池大小）相关数量的任务，避免大量任务集中在单个调度中心集群节点；&#x000A;&#x000A;### 5.5 任务 &quot;运行模式&quot; 剖析&#x000A;#### 5.5.1 &quot;Bean模式&quot; 任务&#x000A;开发步骤：可参考 &quot;章节三&quot; ；&#x000A;原理：每个Bean模式任务都是一个Spring的Bean类实例，它被维护在“执行器”项目的Spring容器中。任务类需要加“@JobHandler(value=&quot;名称&quot;)”注解，因为“执行器”会根据该注解识别Spring容器中的任务。任务类需要继承统一接口“IJobHandler”，任务逻辑在execute方法中开发，因为“执行器”在接收到调度中心的调度请求时，将会调用“IJobHandler”的execute方法，执行任务逻辑。&#x000A;&#x000A;#### 5.5.2 &quot;GLUE模式(Java)&quot; 任务&#x000A;开发步骤：可参考 &quot;章节三&quot; ；&#x000A;原理：每个 &quot;GLUE模式(Java)&quot; 任务的代码，实际上是“一个继承自“IJobHandler”的实现类的类代码”，“执行器”接收到“调度中心”的调度请求时，会通过Groovy类加载器加载此代码，实例化成Java对象，同时注入此代码中声明的Spring服务（请确保Glue代码中的服务和类引用在“执行器”项目中存在），然后调用该对象的execute方法，执行任务逻辑。&#x000A;&#x000A;#### 5.5.3 GLUE模式(Shell) + GLUE模式(Python) + GLUE模式(PHP) + GLUE模式(NodeJS) + GLUE模式(Powershell)&#x000A;开发步骤：可参考 &quot;章节三&quot; ；&#x000A;原理：脚本任务的源码托管在调度中心，脚本逻辑在执行器运行。当触发脚本任务时，执行器会加载脚本源码在执行器机器上生成一份脚本文件，然后通过Java代码调用该脚本；并且实时将脚本输出日志写到任务日志文件中，从而在调度中心可以实时监控脚本运行情况；&#x000A;&#x000A;目前支持的脚本类型如下：&#x000A;&#x000A;    - shell脚本：任务运行模式选择为 &quot;GLUE模式(Shell)&quot;时支持 &quot;Shell&quot; 脚本任务；&#x000A;    - python脚本：任务运行模式选择为 &quot;GLUE模式(Python)&quot;时支持 &quot;Python&quot; 脚本任务；&#x000A;    - php脚本：任务运行模式选择为 &quot;GLUE模式(PHP)&quot;时支持 &quot;PHP&quot; 脚本任务；&#x000A;    - nodejs脚本：任务运行模式选择为 &quot;GLUE模式(NodeJS)&quot;时支持 &quot;NodeJS&quot; 脚本任务；&#x000A;    - powershell：任务运行模式选择为 &quot;GLUE模式(PowerShell)&quot;时支持 &quot;PowerShell&quot; 脚本任务；&#x000A;&#x000A;脚本任务通过 Exit Code 判断任务执行结果，状态码可参考章节 &quot;5.15 任务执行结果说明&quot;；&#x000A;&#x000A;#### 5.5.4 执行器&#x000A;执行器实际上是一个内嵌的Server，默认端口9999（配置项：xxl.job.executor.port）。&#x000A;&#x000A;在项目启动时，执行器会通过“@JobHandler”识别Spring容器中“Bean模式任务”，以注解的value属性为key管理起来。&#x000A;&#x000A;“执行器”接收到“调度中心”的调度请求时，如果任务类型为“Bean模式”，将会匹配Spring容器中的“Bean模式任务”，然后调用其execute方法，执行任务逻辑。如果任务类型为“GLUE模式”，将会加载GLue代码，实例化Java对象，注入依赖的Spring服务（注意：Glue代码中注入的Spring服务，必须存在与该“执行器”项目的Spring容器中），然后调用execute方法，执行任务逻辑。&#x000A;&#x000A;#### 5.5.5 任务日志&#x000A;XXL-JOB会为每次调度请求生成一个单独的日志文件，需要通过 &quot;XxlJobHelper.log&quot; 打印执行日志，“调度中心”查看执行日志时将会加载对应的日志文件。&#x000A;&#x000A;(历史版本通过重写LOG4J的Appender实现，存在依赖限制，该方式在新版本已经被抛弃)&#x000A;&#x000A;日志文件存放的位置可在“执行器”配置文件进行自定义，默认目录格式为：/data/applogs/xxl-job/jobhandler/“格式化日期”/“数据库调度日志记录的主键ID.log”。&#x000A;&#x000A;在JobHandler中开启子线程时，子线程将会将会把日志打印在父线程即JobHandler的执行日志中，方便日志追踪。&#x000A;&#x000A;### 5.6 通讯模块剖析&#x000A;&#x000A;#### 5.6.1 一次完整的任务调度通讯流程 &#x000A;    - 1、“调度中心”向“执行器”发送http调度请求: “执行器”中接收请求的服务，实际上是一台内嵌Server，默认端口9999;&#x000A;    - 2、“执行器”执行任务逻辑；&#x000A;    - 3、“执行器”http回调“调度中心”调度结果: “调度中心”中接收回调的服务，是针对执行器开放一套API服务;&#x000A;&#x000A;#### 5.6.2 通讯数据加密&#x000A;调度中心向执行器发送的调度请求时使用RequestModel和ResponseModel两个对象封装调度请求参数和响应数据, 在进行通讯之前底层会将上述两个对象对象序列化，并进行数据协议以及时间戳检验,从而达到数据加密的功能;&#x000A;&#x000A;### 5.7 任务注册, 任务自动发现   &#x000A;自v1.5版本之后, 任务取消了&quot;任务执行机器&quot;属性, 改为通过任务注册和自动发现的方式, 动态获取远程执行器地址并执行。&#x000A;&#x000A;    AppName: 每个执行器机器集群的唯一标示, 任务注册以 &quot;执行器&quot; 为最小粒度进行注册; 每个任务通过其绑定的执行器可感知对应的执行器机器列表;&#x000A;    注册表: 见&quot;xxl_job_registry&quot;表, &quot;执行器&quot; 在进行任务注册时将会周期性维护一条注册记录，即机器地址和AppName的绑定关系; &quot;调度中心&quot; 从而可以动态感知每个AppName在线的机器列表;&#x000A;    执行器注册: 任务注册Beat周期默认30s; 执行器以一倍Beat进行执行器注册, 调度中心以一倍Beat进行动态任务发现; 注册信息的失效时间为三倍Beat; &#x000A;    执行器注册摘除：执行器销毁时，将会主动上报调度中心并摘除对应的执行器机器信息，提高心跳注册的实时性；&#x000A;    &#x000A;&#x000A;为保证系统&quot;轻量级&quot;并且降低学习部署成本，没有采用Zookeeper作为注册中心，采用DB方式进行任务注册发现；&#x000A;&#x000A;### 5.8 任务执行结果&#x000A;自v1.6.2之后，任务执行结果通过 &quot;IJobHandler&quot; 的返回值 &quot;ReturnT&quot; 进行判断；&#x000A;当返回值符合 &quot;ReturnT.code == ReturnT.SUCCESS_CODE&quot; 时表示任务执行成功，否则表示任务执行失败，而且可以通过 &quot;ReturnT.msg&quot; 回调错误信息给调度中心；&#x000A;从而，在任务逻辑中可以方便的控制任务执行结果；&#x000A;&#x000A;### 5.9 分片广播 &amp; 动态分片   &#x000A;执行器集群部署时，任务路由策略选择&quot;分片广播&quot;情况下，一次任务调度将会广播触发对应集群中所有执行器执行一次任务，同时系统自动传递分片参数；可根据分片参数开发分片任务；&#x000A;&#x000A;&quot;分片广播&quot; 以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。&#x000A;&#x000A;&quot;分片广播&quot; 和普通任务开发流程一致，不同之处在于可以获取分片参数，获取分片参数进行分片业务处理。&#x000A;&#x000A;- Java语言任务获取分片参数方式：BEAN、GLUE模式(Java)&#x000A;```&#x000A;// 可参考Sample示例执行器中的示例任务&quot;ShardingJobHandler&quot;了解试用 &#x000A;int shardIndex = XxlJobHelper.getShardIndex();&#x000A;int shardTotal = XxlJobHelper.getShardTotal();&#x000A;```&#x000A;- 脚本语言任务获取分片参数方式：GLUE模式(Shell)、GLUE模式(Python)、GLUE模式(Nodejs)&#x000A;```&#x000A;// 脚本任务入参固定为三个，依次为：任务传参、分片序号、分片总数。以Shell模式任务为例，获取分片参数代码如下&#x000A;echo &quot;分片序号 index = $2&quot;&#x000A;echo &quot;分片总数 total = $3&quot;&#x000A;```  &#x000A;    &#x000A;分片参数属性说明：&#x000A;&#x000A;    index：当前分片序号(从0开始)，执行器集群列表中当前执行器的序号；&#x000A;    total：总分片数，执行器集群的总机器数量；&#x000A;&#x000A;该特性适用场景如：&#x000A;- 1、分片任务场景：10个执行器的集群来处理10w条数据，每台机器只需要处理1w条数据，耗时降低10倍；&#x000A;- 2、广播任务场景：广播执行器机器运行shell脚本、广播集群节点进行缓存更新等&#x000A;&#x000A;### 5.10 访问令牌（AccessToken）&#x000A;为提升系统安全性，调度中心和执行器进行安全性校验，双方AccessToken匹配才允许通讯；&#x000A;&#x000A;调度中心和执行器，可通过配置项 &quot;xxl.job.accessToken&quot; 进行AccessToken的设置。&#x000A;&#x000A;调度中心和执行器，如果需要正常通讯，只有两种设置；&#x000A;&#x000A;- 设置一：调度中心和执行器，均不设置AccessToken；关闭安全性校验；&#x000A;- 设置二：调度中心和执行器，设置了相同的AccessToken；&#x000A;&#x000A;### 5.11 故障转移 &amp; 失败重试&#x000A;一次完整任务流程包括&quot;调度（调度中心） + 执行（执行器）&quot;两个阶段。&#x000A;    &#x000A;- &quot;故障转移&quot;发生在调度阶段，在执行器集群部署时，如果某一台执行器发生故障，该策略支持自动进行Failover切换到一台正常的执行器机器并且完成调度请求流程。&#x000A;- &quot;失败重试&quot;发生在&quot;调度 + 执行&quot;两个阶段，支持通过自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；&#x000A;&#x000A;### 5.12 执行器灰度上线&#x000A;调度中心与业务解耦，只需部署一次后常年不需要维护。但是，执行器中托管运行着业务作业，作业上线和变更需要重启执行器，尤其是Bean模式任务。&#x000A;执行器重启可能会中断运行中的任务。但是，XXL-JOB得益于自建执行器与自建注册中心，可以通过灰度上线的方式，避免因重启导致的任务中断的问题。&#x000A;&#x000A;步骤如下：&#x000A;- 1、执行器改为手动注册，下线一半机器列表（A组），线上运行另一半机器列表（B组）；&#x000A;- 2、等待A组机器任务运行结束并编译上线；执行器注册地址替换为A组；&#x000A;- 3、等待B组机器任务运行结束并编译上线；执行器注册地址替换为A组+B组；&#x000A;操作结束；&#x000A;&#x000A;### 5.13 任务执行结果说明&#x000A;系统根据以下标准判断任务执行结果，可参考之。&#x000A;&#x000A;-- | Bean/Glue(Java) | Glue(Shell) 等脚本任务&#x000A;--- | --- | ---&#x000A;成功 | IJobHandler.SUCCESS | 0&#x000A;失败 | IJobHandler.FAIL | -1（非0状态码）&#x000A;&#x000A;### 5.14 任务超时控制&#x000A;支持设置任务超时时间，任务运行超时的情况下，将会主动中断任务；&#x000A;&#x000A;需要注意的是，任务超时中断时与任务终止机制（可查看“4.9 终止运行中的任务”）类似，也是通过 &quot;interrupt&quot; 中断任务，因此业务代码需要将 &quot;InterruptedException&quot; 外抛，否则功能不可用。&#x000A;&#x000A;### 5.15 跨语言&#x000A;XXL-JOB是一个跨语言的任务调度平台，主要体现在如下几个方面：&#x000A;- 1、RESTful API：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。（可参考章节 “调度中心/执行器 RESTful API” ）&#x000A;- 2、多任务模式：提供Java、Python、PHP……等十来种任务模式，可参考章节 “5.5 任务 &quot;运行模式&quot; ”；理论上可扩展任意语言任务模式；&#x000A;- 2、提供基于HTTP的任务Handler（Bean任务，JobHandler=&quot;httpJobHandler&quot;）；业务方只需要提供HTTP链接等相关信息即可，不限制语言、平台；（可参考章节 “原生内置Bean模式任务” ）&#x000A;&#x000A;### 5.16 任务失败告警&#x000A;默认提供邮件失败告警，可扩展短信、钉钉等方式。如果需要新增一种告警方式，只需要新增一个实现 &quot;com.xxl.job.admin.core.alarm.JobAlarm&quot; 接口的告警实现即可。可以参考默认提供邮箱告警实现 &quot;EmailJobAlarm&quot;。&#x000A;&#x000A;### 5.17 调度中心Docker镜像构建&#x000A;可以通过以下命令快速构建调度中心，并启动运行；&#x000A;```&#x000A;mvn clean package&#x000A;docker build -t xuxueli/xxl-job-admin ./xxl-job-admin&#x000A;docker run --name xxl-job-admin -p 8080:8080 -d xuxueli/xxl-job-admin&#x000A;```&#x000A;&#x000A;### 5.20 避免任务重复执行   &#x000A;调度密集或者耗时任务可能会导致任务阻塞，集群情况下调度组件小概率情况下会重复触发；&#x000A;针对上述情况，可以通过结合 &quot;单机路由策略（如：第一台、一致性哈希）&quot; + &quot;阻塞策略（如：单机串行、丢弃后续调度）&quot; 来规避，最终避免任务重复执行。 &#x000A;&#x000A;### 5.21 命令行任务   &#x000A;原生提供通用命令行任务Handler（Bean任务，&quot;CommandJobHandler&quot;）；业务方只需要提供命令行即可；&#x000A;如任务参数 &quot;pwd&quot; 将会执行命令并输出数据；&#x000A;&#x000A;### 5.22 日志自动清理&#x000A;XXL-JOB日志主要包含如下两部分，均支持日志自动清理，说明如下：&#x000A;- 调度中心日志表数据：可借助配置项 &quot;xxl.job.logretentiondays&quot; 设置日志表数据保存天数，过期日志自动清理；详情可查看上文配置说明；&#x000A;- 执行器日志文件数据：可借助配置项 &quot;xxl.job.executor.logretentiondays&quot; 设置日志文件数据保存天数，过期日志自动清理；详情可查看上文配置说明；&#x000A;&#x000A;### 5.23 调度结果丢失处理&#x000A;执行器因网络抖动回调失败或宕机等异常情况，会导致任务调度结果丢失。由于调度中心依赖执行器回调来感知调度结果，因此会导致调度日志永远处于 &quot;运行中&quot; 状态。&#x000A;&#x000A;针对该问题，调度中心提供内置组件进行处理，逻辑为：调度记录停留在 &quot;运行中&quot; 状态超过10min，且对应执行器心跳注册失败不在线，则将本地调度主动标记失败；&#x000A;&#x000A;&#x000A;## 六、调度中心/执行器 RESTful API&#x000A;XXL-JOB 目标是一种跨平台、跨语言的任务调度规范和协议。&#x000A;&#x000A;针对Java应用，可以直接通过官方提供的调度中心与执行器，方便快速的接入和使用调度中心，可以参考上文 “快速入门” 章节。&#x000A;&#x000A;针对非Java应用，可借助 XXL-JOB 的标准 RESTful API 方便的实现多语言支持。&#x000A;&#x000A;- 调度中心 RESTful API：&#x000A;    - 说明：调度中心提供给执行器使用的API；不局限于官方执行器使用，第三方可使用该API来实现执行器；&#x000A;    - API列表：执行器注册、任务结果回调等；&#x000A;- 执行器 RESTful API ：&#x000A;    - 说明：执行器提供给调度中心使用的API；官方执行器默认已实现，第三方执行器需要实现并对接提供给调度中心；&#x000A;    - API列表：任务触发、任务终止、任务日志查询……等；&#x000A;&#x000A;此处 RESTful API 主要用于非Java语言定制个性化执行器使用，实现跨语言。除此之外，如果有需要通过API操作调度中心，可以个性化扩展 “调度中心 RESTful API” 并使用。&#x000A;&#x000A;### 6.1 调度中心 RESTful API&#x000A;&#x000A;API服务位置：com.xxl.job.core.biz.AdminBiz （ com.xxl.job.admin.controller.JobApiController ）&#x000A;API服务请求参考代码：com.xxl.job.adminbiz.AdminBizTest&#x000A;&#x000A;#### a、任务回调&#x000A;```&#x000A;说明：执行器执行完任务后，回调任务结果时使用&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{调度中心根地址}/api/callback&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    [{&#x000A;        &quot;logId&quot;:1,              // 本次调度日志ID&#x000A;        &quot;logDateTim&quot;:0,         // 本次调度日志时间&#x000A;        &quot;handleCode&quot;:200,       // 200 表示任务执行正常，500表示失败&#x000A;        &quot;handleMsg&quot;: null&#x000A;        }&#x000A;    }]&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null      // 错误提示消息&#x000A;    }&#x000A;```&#x000A;    &#x000A;#### b、执行器注册&#x000A;```&#x000A;说明：执行器注册时使用，调度中心会实时感知注册成功的执行器并发起任务调度&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{调度中心根地址}/api/registry&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;registryGroup&quot;:&quot;EXECUTOR&quot;,                     // 固定值&#x000A;        &quot;registryKey&quot;:&quot;xxl-job-executor-example&quot;,       // 执行器AppName&#x000A;        &quot;registryValue&quot;:&quot;http://127.0.0.1:9999/&quot;        // 执行器地址，内置服务跟地址&#x000A;    }&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null      // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;#### c、执行器注册摘除&#x000A;```&#x000A;说明：执行器注册摘除时使用，注册摘除后的执行器不参与任务调度与执行&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{调度中心根地址}/api/registryRemove&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;registryGroup&quot;:&quot;EXECUTOR&quot;,                     // 固定值&#x000A;        &quot;registryKey&quot;:&quot;xxl-job-executor-example&quot;,       // 执行器AppName&#x000A;        &quot;registryValue&quot;:&quot;http://127.0.0.1:9999/&quot;        // 执行器地址，内置服务跟地址&#x000A;    }&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null      // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;### 6.2 执行器 RESTful API&#x000A;&#x000A;API服务位置：com.xxl.job.core.biz.ExecutorBiz&#x000A;API服务请求参考代码：com.xxl.job.executorbiz.ExecutorBizTest&#x000A;&#x000A;#### a、心跳检测&#x000A;```&#x000A;说明：调度中心检测执行器是否在线时使用&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{执行器内嵌服务根地址}/beat&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null       // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;#### b、忙碌检测&#x000A;```&#x000A;说明：调度中心检测指定执行器上指定任务是否忙碌（运行中）时使用&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{执行器内嵌服务根地址}/idleBeat&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;jobId&quot;:1       // 任务ID&#x000A;    }&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null       // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;#### c、触发任务&#x000A;```&#x000A;说明：触发任务执行&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{执行器内嵌服务根地址}/run&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;jobId&quot;:1,                                  // 任务ID&#x000A;        &quot;executorHandler&quot;:&quot;demoJobHandler&quot;,         // 任务标识&#x000A;        &quot;executorParams&quot;:&quot;demoJobHandler&quot;,          // 任务参数&#x000A;        &quot;executorBlockStrategy&quot;:&quot;COVER_EARLY&quot;,      // 任务阻塞策略，可选值参考 com.xxl.job.core.enums.ExecutorBlockStrategyEnum&#x000A;        &quot;executorTimeout&quot;:0,                        // 任务超时时间，单位秒，大于零时生效&#x000A;        &quot;logId&quot;:1,                                  // 本次调度日志ID&#x000A;        &quot;logDateTime&quot;:1586629003729,                // 本次调度日志时间&#x000A;        &quot;glueType&quot;:&quot;BEAN&quot;,                          // 任务模式，可选值参考 com.xxl.job.core.glue.GlueTypeEnum&#x000A;        &quot;glueSource&quot;:&quot;xxx&quot;,                         // GLUE脚本代码&#x000A;        &quot;glueUpdatetime&quot;:1586629003727,             // GLUE脚本更新时间，用于判定脚本是否变更以及是否需要刷新&#x000A;        &quot;broadcastIndex&quot;:0,                         // 分片参数：当前分片&#x000A;        &quot;broadcastTotal&quot;:0                          // 分片参数：总分片&#x000A;    }&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null       // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;#### f、终止任务&#x000A;```&#x000A;说明：终止任务&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{执行器内嵌服务根地址}/kill&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;jobId&quot;:1       // 任务ID&#x000A;    }&#x000A;    &#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;      &quot;code&quot;: 200,      // 200 表示正常、其他失败&#x000A;      &quot;msg&quot;: null       // 错误提示消息&#x000A;    }&#x000A;```&#x000A;&#x000A;#### d、查看执行日志&#x000A;```&#x000A;说明：终止任务，滚动方式加载&#x000A;&#x000A;------&#x000A;&#x000A;地址格式：{执行器内嵌服务根地址}/log&#x000A;&#x000A;Header：&#x000A;    XXL-JOB-ACCESS-TOKEN : {请求令牌}&#x000A; &#x000A;请求数据格式如下，放置在 RequestBody 中，JSON格式：&#x000A;    {&#x000A;        &quot;logDateTim&quot;:0,     // 本次调度日志时间&#x000A;        &quot;logId&quot;:0,          // 本次调度日志ID&#x000A;        &quot;fromLineNum&quot;:0     // 日志开始行号，滚动加载日志&#x000A;    }&#x000A;&#x000A;响应数据格式：&#x000A;    {&#x000A;        &quot;code&quot;:200,         // 200 表示正常、其他失败&#x000A;        &quot;msg&quot;: null         // 错误提示消息&#x000A;        &quot;content&quot;:{&#x000A;            &quot;fromLineNum&quot;:0,        // 本次请求，日志开始行数&#x000A;            &quot;toLineNum&quot;:100,        // 本次请求，日志结束行号&#x000A;            &quot;logContent&quot;:&quot;xxx&quot;,     // 本次请求日志内容&#x000A;            &quot;isEnd&quot;:true            // 日志是否全部加载完&#x000A;        }&#x000A;    }&#x000A;```&#x000A;&#x000A;&#x000A;&#x000A;## 七、版本更新日志&#x000A;### 7.1 版本 V1.1.x，新特性[2015-12-05]&#x000A;**【于V1.1.x版本，XXL-JOB正式应用于我司，内部定制别名为 “Ferrari”，新接入应用推荐使用最新版本】**&#x000A;- 1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；&#x000A;- 2、动态：支持动态修改任务状态，动态暂停/恢复任务，即时生效；&#x000A;- 3、服务HA：任务信息持久化到mysql中，Job服务天然支持集群，保证服务HA；&#x000A;- 4、任务HA：某台Job服务挂掉，任务会平滑分配给其他的某一台存活服务，即使所有服务挂掉，重启时或补偿执行丢失任务；&#x000A;- 5、一个任务只会在其中一台服务器上执行；&#x000A;- 6、任务串行执行；&#x000A;- 7、支持自定义参数；&#x000A;- 8、支持远程任务执行终止；&#x000A;&#x000A;### 7.2 版本 V1.2.x，新特性[2016-01-17]&#x000A;- 1、支持任务分组；&#x000A;- 2、支持“本地任务”、“远程任务”；&#x000A;- 3、底层通讯支持两种方式，Servlet方式 + JETTY方式；&#x000A;- 4、支持“任务日志”；&#x000A;- 5、支持“串行执行”，并行执行；&#x000A;	&#x000A;	说明：V1.2版本将系统架构按功能拆分为：&#x000A;	&#x000A;		- 调度模块（调度中心）：负责管理调度信息，按照调度配置发出调度请求；&#x000A;		- 执行模块（执行器）：负责接收调度请求并执行任务逻辑；&#x000A;		- 通讯模块：负责调度模块和任务模块之间的信息通讯；&#x000A;	优点：&#x000A;	&#x000A;		- 解耦：任务模块提供任务接口，调度模块维护调度信息，业务相互独立；&#x000A;		- 高扩展性；&#x000A;		- 稳定性；&#x000A;&#x000A;### 7.3 版本 V1.3.0，新特性[2016-05-19]&#x000A;- 1、遗弃“本地任务”模式，推荐使用“远程任务”，易于系统解耦，任务对应的JobHandler统称为“执行器”；&#x000A;- 2、遗弃“servlet”方式底层系统通讯，推荐使用JETTY方式，调度+回调双向通讯，重构通讯逻辑；&#x000A;- 3、UI交互优化：左侧菜单展开状态优化，菜单项选中状态优化，任务列表打开表格有压缩优化；&#x000A;- 4、【重要】“执行器”细分为：BEAN、GLUE两种开发模式，简介见下文：&#x000A;	&#x000A;	“执行器” 模式简介：&#x000A;		- BEAN模式执行器：每个执行器都是Spring的一个Bean实例，XXL-JOB通过注解@JobHandler识别和调度执行器；&#x000A;		 -GLUE模式执行器：每个执行器对应一段代码，在线Web编辑和维护，动态编译生效，执行器负责加载GLUE代码和执行；&#x000A;&#x000A;### 7.4 版本 V1.3.1，新特性[2016-05-23]&#x000A;- 1、更新项目目录结构：&#x000A;	- /xxl-job-admin -------------------- 【调度中心】：负责管理调度信息，按照调度配置发出调度请求；&#x000A;	- /xxl-job-core ----------------------- 公共依赖&#x000A;	- /xxl-job-executor-example ------ 【执行器】：负责接收调度请求并执行任务逻辑；&#x000A;	- /db ---------------------------------- 建表脚本&#x000A;	- /doc --------------------------------- 用户手册&#x000A;- 2、在新的目录结构上，升级了用户手册；&#x000A;- 3、优化了一些交互和UI；&#x000A;&#x000A;### 7.5 版本 V1.3.2，新特性[2016-05-28]&#x000A;- 1、调度逻辑进行事务包裹；&#x000A;- 2、执行器异步回调执行日志；&#x000A;- 3、【重要】在 “调度中心” 支持HA的基础上，扩展执行器的Failover支持，支持配置多执行期地址；&#x000A;&#x000A;### 7.6 版本 V1.4.0 新特性[2016-07-24]&#x000A;- 1、任务依赖: 通过事件触发方式实现, 任务执行成功并回调时会主动触发一次子任务的调度, 多个子任务用逗号分隔;&#x000A;- 2、执行器底层实现代码进行重度重构, 优化底层建表脚本;&#x000A;- 3、执行器中任务线程分组逻辑优化: 之前根据执行器JobHandler进行线程分组,当多个任务复用Jobhanlder会导致相互阻塞。现改为根据调度中心任务进行任务线程分组,任务与任务执行相互隔离;&#x000A;- 4、执行器调度通讯方案优化, 通过Hex + HC实现建议RPC通讯协议, 优化了通讯参数的维护和解析流程;&#x000A;- 5、调度中心, 新建/编辑任务, 界面属性调整: &#x000A;    - 5.1、任务新增/编辑界面中去除 &quot;任务名JobName&quot;属性 ,该属性改为系统自动生成: 该字段之前主要用于在 &quot;调度中心&quot; 唯一标示一个任务, 现实意义不大, 因此计划淡化掉该字段,改为系统生成UUID,从而简化任务新建的操作;&#x000A;    - 5.2、任务新增/编辑界面中去除 &quot;GLUE模式&quot; 复选框位置调整, 改为贴近&quot;JobHandler&quot;输入框右侧;&#x000A;    - 5.3、任务新增/编辑界面中去除 &quot;报警阈值&quot; 属性;&#x000A;    - 5.4、任务新增/编辑界面中去除 &quot;子任务Key&quot; 属性, 每个任务全局任务Key可以从任务列表获取, 当本任务执行结束且成功后, 将会根据子任务Key匹配子任务并主动触发一次子任务执行;&#x000A;- 6、问题修复:&#x000A;    - 6.1、执行器jetty关闭优化,解决一处可能导致jetty无法关闭的问题;&#x000A;    - 6.2、执行器任务终止时,执行队列回调优化,解决一处导致任务无法回调的问题；&#x000A;    - 6.3、调度中心中列表分页参数优化,解决一处因服务器限制post长度而引起的问题;&#x000A;    - 6.4、执行器Jobhandler注解优化,解决一处因事务代理导致的容器无法加载JobHandler的问题;&#x000A;    - 6.5、远程调度优化,禁用retry策略,解决一处可能导致重复调用的问题;&#x000A;&#x000A;Tips: 历史版本(V1.3.x)目前已经Release至稳定版本, 进入维护阶段, 地址见分支 [V1.3](https://github.com/xuxueli/xxl-job/tree/v1.3) 。新特性将会在master分支持续更新。&#x000A;&#x000A;### 7.7 版本 V1.4.1 新特性[2016-09-06]&#x000A;- 1、项目成功推送maven中央仓库, 中央仓库地址以及依赖如下: &#x000A;    ```&#x000A;    &lt;!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ --&gt;&#x000A;    &lt;dependency&gt;&#x000A;        &lt;groupId&gt;com.xuxueli&lt;/groupId&gt;&#x000A;        &lt;artifactId&gt;xxl-job-core&lt;/artifactId&gt;&#x000A;        &lt;version&gt;${最新稳定版}&lt;/version&gt;&#x000A;    &lt;/dependency&gt;&#x000A;    ```&#x000A;- 2、为适配中央仓库规则, 项目groupId从com.xxl改为com.xuxueli。&#x000A;- 3、系统版本不在维护在项目跟pom中,各个子模块单独配置版本配置,解决子模块无法单独编译的问题;&#x000A;- 4、底层RPC通讯,传输数据的字节长度统计规则优化,可节省50%数据传输量;&#x000A;- 5、IJobHandler取消任务返回值,原通过返回值判断执行状态,逻辑改为:默认任务执行成功,仅在捕获异常时认定任务执行失败。&#x000A;- 6、系统公共弹框功能,插件化;&#x000A;- 7、底层表结构,表明统一大写;&#x000A;- 8、调度中心,异常处理器JSON响应的ContentType修改,修复浏览器不识别的问题;&#x000A;&#x000A;### 7.8 版本 V1.4.2 新特性[2016-09-29]&#x000A;- 1、推送新版本 V1.4.2 至中央仓库, 大版本 V1.4 进入维护阶段;&#x000A;- 2、任务新增时,任务列表偏移问题修复;&#x000A;- 3、修复一处因bootstrap不支持模态框重叠而导致的样式错乱的问题, 在任务编辑时会出现该问题;&#x000A;- 4、调度超时和Handler匹配不到时,调度状态优化;&#x000A;- 5、因catch异常,导致任务不可终止的问题,给出解决方案, 见文档;&#x000A;&#x000A;### 7.9 版本 V1.5.0 特性[2016-11-13]&#x000A;- 1、任务注册: 执行器会周期性自动注册任务, 调度中心将会自动发现注册的任务并触发执行。&#x000A;- 2、&quot;执行器&quot; 新增参数 &quot;AppName&quot; : 是每个执行器集群的唯一标示AppName, 并周期性以AppName为对象进行自动注册。&#x000A;- 3、调度中心新增栏目 &quot;执行器管理&quot; : 管理在线的执行器, 通过属性AppName自动发现注册的执行器。只有被管理的执行器才允许被使用;&#x000A;- 4、&quot;任务组&quot;属性改为&quot;执行器&quot;: 每个任务需要绑定指定的执行器, 调度地址通过绑定的执行器获取;&#x000A;- 5、抛弃&quot;任务机器&quot;属性: 通过任务绑定的执行器, 自动发现注册的远程执行器地址并触发调度请求。&#x000A;- 6、&quot;公共依赖&quot;中新增DBGlueLoader,基于原生jdbc实现GLUE源码的加载器,减少第三方依赖(mybatis,spring-orm等);精简和优化执行器测配置(针对GLUE任务),降低上手难度;&#x000A;- 7、表结构调整,底层重构优化;&#x000A;- 8、&quot;调度中心&quot;自动注册和发现,failover: 调度中心周期性自动注册, 任务回调时可以感知在线的所有调度中心地址, 通过failover的方式进行任务回调,避免回调单点风险。&#x000A;&#x000A;### 7.10 版本 V1.5.1 特性[2016-11-13]&#x000A;- 1、底层代码重构和逻辑优化，POM清理以及CleanCode；&#x000A;- 2、Servlet/JSP Spec设定为3.0/2.2&#x000A;- 3、Spring升级至3.2.17.RELEASE版本；&#x000A;- 4、Jetty升级版本至8.2.0.v20160908；&#x000A;- 5、已推送V1.5.0和V1.5.1至Maven中央仓库；&#x000A;&#x000A;### 7.11 版本 V1.5.2 特性[2017-02-28]&#x000A;- 1、IP工具类获取IP逻辑优化，IP静态缓存；&#x000A;- 2、执行器、调度中心，均支持自定义注册IP地址；解决机器多网卡时错误网卡注册的情况；&#x000A;- 3、任务跨天执行时生成多份日志文件的问题修复；&#x000A;- 4、底层日志底层日志调整，非敏感日志level调整为debug；&#x000A;- 5、升级数据库连接池c3p0版本；&#x000A;- 6、执行器log4j配置优化，去除无效属性；&#x000A;- 7、底层代码重构和逻辑优化以及CleanCode；&#x000A;- 8、GLUE依赖注入逻辑优化，支持别名注入；&#x000A;&#x000A;### 7.12 版本 V1.6.0 特性[2017-03-13]&#x000A;- 1、通讯方案升级，原基于HEX的通讯模型调整为基于HTTP的B-RPC的通讯模型；&#x000A;- 2、执行器支持手动设置执行地址列表，提供开关切换使用注册地址还是手动设置的地址；&#x000A;- 3、执行器路由规则：第一个、最后一个、轮询、随机、一致性HASH、最不经常使用、最近最久未使用、故障转移；&#x000A;- 4、规范线程模型统一，统一线程销毁方案(通过listener或stop方法，容器销毁时销毁线程；Daemon方式有时不太理想)；&#x000A;- 5、规范系统配置数据，通过配置文件统一管理；&#x000A;- 6、CleanCode，清理无效的历史参数；&#x000A;- 7、底层扩展数据结构以及相关表结构调整；&#x000A;- 8、新建任务默认为非运行状态；&#x000A;- 9、GLUE模式任务实例更新逻辑优化，原根据超时时间更新改为根据版本号更新，源码变动版本号加一；&#x000A;&#x000A;### 7.13 版本 V1.6.1 特性[2017-03-25]&#x000A;- 1、Rolling日志；&#x000A;- 2、WebIDE交互重构；&#x000A;- 3、通讯增强校验，有效过滤非正常请求；&#x000A;- 4、权限增强校验，采用动态登录TOKEN（推荐接入内部SSO）；&#x000A;- 5、数据库配置优化，解决乱码问题；&#x000A;&#x000A;### 7.14 版本 V1.6.2 特性[2017-04-25]&#x000A;- 1、运行报表：支持实时查看运行数据，如任务数量、调度次数、执行器数量等；以及调度报表，如调度日期分布图，调度成功分布图等；&#x000A;- 2、JobHandler支持设置任务返回值，在任务逻辑中可以方便的控制任务执行结果；&#x000A;- 3、资源路径包含空格或中文时资源文件无法加载时，无法准确查看异常信息的问题处理。&#x000A;- 4、路由策越优化：循环和LFU路由策略计数器自增无上限问题和首次路由压力集中在首台机器的问题修复；&#x000A;&#x000A;### 7.15 版本 V1.7.0 特性[2017-05-02]&#x000A;- 1、脚本任务：支持以GLUE模式开发和运行脚本任务，包括Shell、Python和Groovy等类型脚本;&#x000A;- 2、新增spring-boot类型执行器example项目；&#x000A;- 3、升级jetty版本至9.2；&#x000A;- 4、任务运行日志移除log4j组件依赖，改为底层自主实现，从而取消了对日志组件的依赖限制；&#x000A;- 5、执行器移除GlueLoader依赖，改为推送方式实现，从而GLUE源码加载不再依赖JDBC；&#x000A;- 6、登录拦截Redirect时获取项目名，解决非根据目录发布时跳转404问题；&#x000A;&#x000A;### 7.16 版本 V1.7.1 特性[2017-05-08]&#x000A;- 1、运行日志读写编码统一为UTF-8，解决windows环境下日志乱码问题；&#x000A;- 2、通讯超时时间限定为10s，避免异常情况下调度线程占用；&#x000A;- 3、执行器，server启动、销毁和注册逻辑调整；&#x000A;- 4、JettyServer关闭逻辑优化，修复执行器无法正常关闭导致端口占用和频繁打印c3p0日志的问题；&#x000A;- 5、JobHandler中开启子线程时，支持子线程输出执行日志并通过Rolling查看。&#x000A;- 6、任务日志清理功能；&#x000A;- 7、弹框组件统一替换为layer；&#x000A;- 8、升级quartz版本至2.3.0；&#x000A;&#x000A;### 7.17 版本 V1.7.2 特性[2017-05-17]&#x000A;- 1、阻塞处理策略：调度过于密集执行器来不及处理时的处理策略，策略包括：单机串行（默认）、丢弃后续调度、覆盖之前调度；&#x000A;- 2、失败处理策略；调度失败时的处理策略，策略包括：失败告警（默认）、失败重试；&#x000A;- 3、通讯时间戳超时时间调整为180s；&#x000A;- 4、执行器与数据库彻底解耦，但是执行器需要配置调度中心集群地址。调度中心提供API供执行器回调和心跳注册服务，取消调度中心内部jetty，心跳周期调整为30s，心跳失效为三倍心跳；&#x000A;- 5、执行参数编辑时丢失问题修复；&#x000A;- 6、新增任务测试Demo，方便在开发时进行任务逻辑测试；&#x000A;&#x000A;### 7.18 版本 V1.8.0 特性[2017-07-17]&#x000A;- 1、任务Cron更新逻辑优化，改为rescheduleJob，同时防止cron重复设置；&#x000A;- 2、API回调服务失败状态码优化，方便问题排查；&#x000A;- 3、XxlJobLogger的日志多参数支持；&#x000A;- 4、路由策略新增 &quot;忙碌转移&quot; 模式：按照顺序依次进行空闲检测，第一个空闲检测成功的机器选定为目标执行器并发起调度；&#x000A;- 5、路由策略代码重构；&#x000A;- 6、执行器重复注册问题修复；&#x000A;- 7、任务线程轮空30次后自动销毁，降低低频任务的无效线程消耗。&#x000A;- 8、执行器任务执行结果批量回调，降低回调频率提升执行器性能；&#x000A;- 9、springboot版本执行器，取消XML配置，改为类配置方式；&#x000A;- 10、执行日志，支持根据运行 &quot;状态&quot; 筛选日志；&#x000A;- 11、调度中心任务注册检测逻辑优化；&#x000A;&#x000A;### 7.19 版本 V1.8.1 特性[2017-07-30]&#x000A;- 1、分片广播任务：执行器集群部署时，任务路由策略选择&quot;分片广播&quot;情况下，一次任务调度将会广播触发集群中所有执行器执行一次任务，可根据分片参数处理分片任务；&#x000A;- 2、动态分片：分片广播任务以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。&#x000A;- 3、执行器JobHandler禁止命名冲突；&#x000A;- 4、执行器集群地址列表进行自然排序；&#x000A;- 5、调度中心，DAO层代码精简优化并且新增测试用例覆盖；&#x000A;- 6、调度中心API服务改为自研RPC形式，统一底层通讯模型；&#x000A;- 7、新增调度中心API服务测试Demo，方便在调度中心API扩展和测试；&#x000A;- 8、任务列表页交互优化，更换执行器分组时自动刷新任务列表，新建任务时默认定位在当前执行器位置；&#x000A;- 9、访问令牌（accessToken）：为提升系统安全性，调度中心和执行器进行安全性校验，双方AccessToken匹配才允许通讯；&#x000A;- 10、springboot版本执行器，升级至1.5.6.RELEASE版本；&#x000A;- 11、统一maven依赖版本管理；&#x000A;&#x000A;### 7.20 版本 V1.8.2 特性[2017-09-04]&#x000A;- 1、项目主页搭建：提供中英文文档：https://www.xuxueli.com/xxl-job &#x000A;- 2、JFinal执行器Sample示例项目；&#x000A;- 3、事件触发：除了&quot;Cron方式&quot;和&quot;任务依赖方式&quot;触发任务执行之外，支持基于事件的触发任务方式。调度中心提供触发任务单次执行的API服务，可根据业务事件灵活触发。&#x000A;- 4、执行器摘除：执行器销毁时，主动通知调度中心并摘除对应执行器节点，提高执行器状态感知的时效性。&#x000A;- 5、执行器手动设置IP时将会绑定Host；&#x000A;- 6、规范项目目录，方便扩展多执行器；&#x000A;- 7、解决执行器回调URL不支持配置HTTPS时问题；&#x000A;- 8、执行器回调线程销毁前, 批量回调队列中数据，防止任务结果丢失；&#x000A;- 9、调度中心任务监控线程销毁时，批量对失败任务告警，防止告警信息丢失；&#x000A;- 10、任务日志文件路径时间戳格式化时SimpleDateFormat并发问题解决；&#x000A;&#x000A;### 7.21 版本 V1.9.0 特性[2017-12-29]&#x000A;- 1、新增Nutz执行器Sample示例项目；&#x000A;- 2、新增任务运行模式 &quot;GLUE模式(NodeJS) &quot;，支持NodeJS脚本任务；&#x000A;- 3、脚本任务Shell、Python和Nodejs等支持获取分片参数；&#x000A;- 4、失败重试，完整支持：调度中心调度失败且启用&quot;失败重试&quot;策略时，将会自动重试一次；执行器执行失败且回调失败重试状态（新增失败重试状态返回值）时，也将会自动重试一次；&#x000A;- 5、失败告警策略扩展：默认提供邮件失败告警，可扩展短信等，扩展代码位置为 &quot;JobFailMonitorHelper.failAlarm&quot;；&#x000A;- 6、执行器端口支持自动生成(小于等于0时)，避免端口定义冲突；&#x000A;- 7、调度报表优化，支持时间区间筛选；&#x000A;- 8、Log组件支持输出异常栈信息，底层实现优化；&#x000A;- 9、告警邮件样式优化，调整为表格形式，邮件组件调整为commons-email简化邮件操作；&#x000A;- 10、项目依赖全量升级至较新稳定版本，如spring、jackson等等；&#x000A;- 11、任务日志，记录发起调度的机器信息；&#x000A;- 12、交互优化，如登录注销；&#x000A;- 13、任务Cron长度扩展支持至128位，支持负责类型Cron设置；&#x000A;- 14、执行器地址录入交互优化，地址长度扩展支持至512位，支持大规模执行器集群配置；&#x000A;- 15、任务参数“IJobHandler.execute”入参改为“String params”，增强入参通用性。&#x000A;- 16、IJobHandler提供init/destroy方法，支持在相应任务线程初始化和销毁时进行附加操作；&#x000A;- 17、任务注解调整为 “@JobHandler”，与任务抽象接口统一；&#x000A;- 18、修复任务监控线程被耗时任务阻塞的问题；&#x000A;- 19、修复任务监控线程无法监控任务触发和执行状态均未0的问题；&#x000A;- 20、执行器动态代理对象，拦截非业务方法的执行；&#x000A;- 21、修复JobThread捕获Error错误不更新JobLog的问题；&#x000A;- 22、修复任务列表界面左侧菜单合并时样式错乱问题；&#x000A;- 23、调度中心项目日志配置改为xml文件格式；&#x000A;- 24、Log地址格式兼容，支持非&quot;/&quot;结尾路径配置；&#x000A;- 25、底层系统日志级别规范调整，清理遗留代码；&#x000A;- 26、建表SQL优化，支持同步创建制定编码的库和表；&#x000A;- 27、系统安全性优化，登录Token写Cookie时进行MD5加密，同时Cookie启用HttpOnly；&#x000A;- 28、新增&quot;任务ID&quot;属性，移除&quot;JobKey&quot;属性，前者承担所有功能，方便后续增强任务依赖功能。&#x000A;- 29、任务循环依赖问题修复，避免子任务与父任务重复导致的调度死循环；&#x000A;- 30、任务列表新增筛选条件 &quot;任务描述&quot;，快速检索任务；&#x000A;- 31、执行器Log文件定期清理功能：执行器新增配置项（&quot;xxl.job.executor.logretentiondays&quot;）日志保存天数，日志文件过期自动删除。&#x000A;&#x000A;### 7.22 版本 V1.9.1 特性[2018-02-22]&#x000A;- 1、国际化：调度中心实现国际化，支持中文、英文两种语言，默认为中文。&#x000A;- 2、调度报表新增&quot;运行中&quot;中状态项；&#x000A;- 3、调度报表优化，报表SQL调优并且新增LocalCache缓存（缓存时间60s），提高大数据量下报表加载速度；&#x000A;- 4、修复打包部署时资源文件乱码问题；&#x000A;- 5、修复新版本chrome滚动到顶部失效问题；&#x000A;- 6、调度中心配置加载优化，取消对配置文件名的强依赖，支持加载磁盘配置；&#x000A;- 7、修复脚本任务Log文件未正常close的问题；&#x000A;- 8、项目依赖全量升级至较新稳定版本，如spring、jackson等等；&#x000A;&#x000A;### 7.23 版本 V1.9.2 特性[2018-10-05]&#x000A;- 1、任务超时控制：新增任务属性 &quot;任务超时时间&quot;，并支持自定义，任务运行超时将会主动中断任务；&#x000A;- 2、任务失败重试次数：新增任务属性 &quot;失败重试次数&quot;，并支持自定义，当任务失败时将会按照预设的失败重试次数主动进行重试；同时收敛废弃其他失败重试策略，如调度失败、执行失败、状态码失败等；&#x000A;- 3、新增任务运行模式 &quot;GLUE模式(PHP) &quot;，支持php脚本任务；&#x000A;- 4、新增任务运行模式 &quot;GLUE模式(PowerShell) &quot;，支持PowerShell脚本任务；&#x000A;- 5、调度全异步处理：任务触发之后，推送到调度队列，多线程并发处理调度请求，提高任务调度速率的同时，避免因网络问题导致quartz调度线程阻塞的问题；&#x000A;- 6、执行器任务结果落盘优化：执行器回调失败时将任务结果写磁盘，待重启或网络恢复时重试回调任务结果，防止任务执行结果丢失；&#x000A;- 7、任务日志查询速度大幅提升：百万级别数据量搜索速度提升1000倍；&#x000A;- 8、调度中心提供API服务，支持通过API服务对任务进行查询、新增、更新、启停等操作；&#x000A;- 9、底层自研Log组件参数占位符改为&quot;{}&quot;，并修复打印有参日志时参数不匹配导致报错的问题；&#x000A;- 10、任务回调结果优化，支持展示在Rolling log中，方便问题排查；&#x000A;- 11、底层LocalCache组件兼容性优化，支持jdk9、jdk10及以上版本编译部署；&#x000A;- 12、告警邮件固定使用 UTF-8 编码格式，修复由机器编码导致的邮件乱码问题；&#x000A;- 13、告警邮件中展示失败告警信息；&#x000A;- 14、告警邮箱支持SSL配置；&#x000A;- 15、Window机器下File.separator不兼容问题修复；&#x000A;- 16、脚本任务异常Log输出优化；&#x000A;- 17、任务线程停止变量修饰符优化；&#x000A;- 18、脚本任务Log文件流关闭优化；&#x000A;- 19、任务报表成功、失败和进行中统计问题修复；&#x000A;- 20、核心依赖Core内部国际化处理；&#x000A;- 21、默认Quartz线程数调整为50；&#x000A;- 22、新增左侧菜单&quot;运行报表&quot;；&#x000A;- 23、执行器手动设置IP时取消绑定Host的操作，该IP仅供执行器注册使用；修复指定外网IP时无法绑定执行器Host的问题；&#x000A;- 24、取消父子任务不可重复的限制，支持循环任务触发等特殊场景；&#x000A;- 25、任务调度备注中标注任务触发类型，如Cron触发、父任务触发、API触发等等，方便排查调度日志；&#x000A;- 26、底层日志组件SimpleDateFormat线程安全问题修复；&#x000A;- 27、执行器通讯线程优化，corePoolSize从256降低至32；&#x000A;- 28、任务日志表状态字段类型优化；&#x000A;- 29、GLUE脚本文件自动清理功能，及时清理过期脚本文件；&#x000A;- 30、执行器注册方式切换优化，切换自动注册时主动同步在线机器，避免执行器为空的问题；&#x000A;- 31、跨平台：除了提供Java、Python、PHP等十来种任务模式之外，新增提供基于HTTP的任务模式；&#x000A;- 32、底层RPC序列化协议调整为hessian2；&#x000A;- 33、修复表字段 “t.order”与数据库关键字冲突查询失败的问题，&#x000A;- 34、任务属性枚举 &quot;任务模式、阻塞策略&quot; 国际化优化；&#x000A;- 35、分片任务失败重试优化，仅重试当前失败的分片；&#x000A;- 36、任务触发时支持动态传参，调度中心与API服务均提供提供动态参数功能；&#x000A;- 37、任务执行日志、调度日志字段类型调整，改为text类型并取消字数限制；&#x000A;- 38、GLUE任务脚本字段类型调整，改为mediumtext类型，提高GLUE长度上限；&#x000A;- 39、任务监控线程Log输出优化，运行中任务的监控Log改为debug级别，减少非核心日志量；&#x000A;- 40、项目依赖全量升级至较新稳定版本，如spring、Jackson、groovy等等；&#x000A;- 41、docker支持：调度中心提供 Dockerfile 方便快速构建docker镜像； &#x000A;&#x000A;### 7.24 版本 V2.0.0 Release Notes[2018-11-04]&#x000A;- 1、调度中心迁移到 springboot；&#x000A;- 2、底层通讯组件迁移至 xxl-rpc；&#x000A;- 3、容器化：提供官方docker镜像，并实时更新推送dockerhub（docker pull xuxueli/xxl-job-admin），进一步实现产品开箱即用；&#x000A;- 4、新增无框架执行器Sample示例项目 &quot;xxl-job-executor-sample-frameless&quot;。不依赖第三方框架，只需main方法即可启动运行执行器；&#x000A;- 5、命令行任务：原生提供通用命令行任务Handler（Bean任务，&quot;CommandJobHandler&quot;）；业务方只需要提供命令行即可；&#x000A;- 6、任务状态优化，仅运行状态&quot;NORMAL&quot;任务关联至quartz，降低quartz底层数据存储与调度压力；&#x000A;- 7、任务状态规范：新增任务默认停止状态，任务更新时保持任务状态不变；&#x000A;- 8、IP获取逻辑优化，优先遍历网卡来获取可用IP；&#x000A;- 9、任务新增的API服务接口返回任务ID，方便调用方实用；&#x000A;- 10、组件化优化，移除对 spring 的依赖：非spring应用选用 &quot;XxlJobExecutor&quot; 、spring应用选用 &quot;XxlJobSpringExecutor&quot; 作为执行器组件； &#x000A;- 11、任务RollingLog展示逻辑优化，修复超时任务无法查看的问题；&#x000A;- 12、多项UI组件升级到最新版本，如：CodeMirror、Echarts、Jquery 等；&#x000A;- 13、项目依赖升级 groovy 至较新稳定版本；pom清理；&#x000A;- 14、子任务失败重试重试逻辑优化，子任务失败时将会按照其预设的失败重试次数主动进行重试&#x000A;&#x000A;### 7.25 版本 v2.0.1 Release Notes[2018-11-09]&#x000A;- 1、左侧菜单折叠动画问题修复；&#x000A;- 2、调度报表日期分布图默认值统一；&#x000A;- 3、freemarker对数字默认加千分位问题修复，解决日志ID被分隔导致查看日志失败问题；&#x000A;- 4、底层通讯组件升级，修复通讯异常时无效等待的问题；&#x000A;- 5、执行器启动之后jetty停止的问题修复；&#x000A;&#x000A;### 7.26 版本 v2.0.2 Release Notes[2019-04-20]&#x000A;- 1、底层通讯方案优化：升级较新版本xxl-rpc，由&quot;JETTY&quot;方案调整为&quot;NETTY_HTTP&quot;方案，执行器内嵌netty-http-server提供服务，调度中心复用容器端口提供服务；&#x000A;- 2、任务告警逻辑调整，改为通过扫描失败日志方式触发。一方面精确扫描失败任务，降低扫描范围；另一方面取消内存队列，降低线程内存消耗；&#x000A;- 3、Quartz触发线程池废弃并替换为 &quot;XxlJobThreadPool&quot;，降低线程切换、内存占用带来的消耗，提高调度性能；&#x000A;- 4、调度线程池隔离，拆分为&quot;Fast&quot;和&quot;Slow&quot;两个线程池，1分钟窗口期内任务耗时达500ms超过10次，该窗口期内判定为慢任务，慢任务自动降级进入&quot;Slow&quot;线程池，避免耗尽调度线程，提高系统稳定性；&#x000A;- 5、执行器热部署时JobHandler重新初始化，修复由此导致的 &quot;jobhandler naming conflicts.&quot; 问题；&#x000A;- 6、新增Class的加载缓存，解决频繁加载Class会使jvm的方法区空间不足导致OOM的问题；&#x000A;- 7、任务支持更换绑定执行器，方便任务分组转移和管理；&#x000A;- 8、调度中心告警邮件发送组件改为 “spring-boot-starter-mail”；&#x000A;- 9、记住密码功能优化，选中时永久记住；非选中时关闭浏览器即登出；&#x000A;- 10、项目依赖升级至较新稳定版本，如quartz、spring、jackson、groovy、xxl-rpc等等；&#x000A;- 11、精简项目，取消第三方依赖，如 commons-collections4、commons-lang3 ;&#x000A;- 12、执行器回调日志落盘方案复用RPC序列化方案，并移除Jackson依赖；&#x000A;- 13、底层Log调优，应用正常终止取消异常栈信息打印；&#x000A;- 14、交互优化，尽量避免新开页面窗口；仅WebIDE支持新开页，并提供窗口快速关闭按钮；任务启、停、删除、触发等轻操作提示改为toast方式，&#x000A;- 15、任务暂停、删除优化，避免quartz delete不完整导致任务脏数据；&#x000A;- 16、任务回调、心跳注册成功日志优化，非核心常规日志调整为debug级别，降低冗余日志输出；&#x000A;- 17、调整首页报表默认区间为本周，避免日志量太大查询缓慢；&#x000A;- 18、LRU路由更新不及时问题修复；&#x000A;- 19、任务失败告警邮件发送逻辑优化；&#x000A;- 20、调度日志排序逻辑调整为按照调度时间倒序，兼容TIDB等主键不连续日志存储组件；&#x000A;- 21、执行器优雅停机优化；&#x000A;- 22、连接池配置优化，增强连接有效性验证；&#x000A;- 23、JobHandler#msg长度限制，修复异常情况下日志超长导致内存溢出的问题；&#x000A;- 24、升级xxl-rpc至较新版本，修复springboot 2.x版本兼容性问题；&#x000A;&#x000A;### 7.27 版本 v2.1.0 Release Notes[2019-07-07]&#x000A;- 1、自研调度组件，移除quartz依赖：一方面是为了精简系统降低冗余依赖，另一方面是为了提供系统的可控度与稳定性；&#x000A;    - 触发：单节点周期性触发，运行事件如delayqueue；&#x000A;    - 调度：集群竞争，负载方式协同处理，锁竞争-更新触发信息-推送时间轮-锁释放-锁竞争；&#x000A;- 2、底层表结构重构：移除11张quartz相关表，并对现有表结构优化梳理；&#x000A;- 3、任务日志主键调整为long数据类型，防止海量日志情况下数据溢出；&#x000A;- 4、底层线程模型重构：移除Quartz线程池，降低系统线程与内存开销；&#x000A;- 5、用户管理：支持在线管理系统用户，存在管理员、普通用户两种角色；&#x000A;- 6、权限管理：执行器维度进行权限控制，管理员拥有全量权限，普通用户需要分配执行器权限后才允许相关操作；&#x000A;- 7、调度线程池参数调优；&#x000A;- 8、注册表索引优化，缓解锁表问题；&#x000A;- 9、新增Jboot执行器Sample示例项目；&#x000A;- 10、任务列表优化，支持根据 &quot;任务状态&quot;、&quot;负责人&quot; 属性筛选任务；&#x000A;- 11、任务日志列表交互优化，操作按钮合并为分割按钮；&#x000A;- 12、项目依赖升级至较新稳定版本，如spring、springboot、groovy、xxl-rpc等等；并清理冗余POM；&#x000A;- 13、升级xxl-rpc至较新版本，修复代理服务初始化时远程服务不可用导致长连冗余创建的问题;&#x000A;- 14、首页调度报表的日期排序在TIDB下乱序问题修复；&#x000A;- 15、调度中心与执行器双向通讯超时时间调整为3s；&#x000A;- 16、调度组件销毁流程优化，先停止调度线程，然后等待时间轮内存量任务处理完成，最终销毁时间轮线程；&#x000A;- 17、执行器回调线程优化，回调地址为空时销毁问题修复；&#x000A;- 18、HttpJobHandler优化，响应数据指定UTF-8格式，避免中文乱码；&#x000A;- 19、代码优化，ConcurrentHashMap变量类型改为ConcurrentMap，避免因不同版本实现不同导致的兼容性问题；&#x000A;&#x000A;### 7.28 版本 v2.1.1 Release Notes[2019-11-24]&#x000A;- 1、 调度中心日志自动清理功能（至此，调度中心/执行器均支持日志自动清理，过期天数均默认设置为30天）：调度中心新增配置项（&quot;xxl.job.logretentiondays&quot;）日志保存天数，过期日志自动清理；解决海量日志情况下日志表慢SQL问题；限制大于等于7时生效，否则关闭清理功能，默认为30；&#x000A;- 2、 调度报表优化：新增日志报表的存储表，三天内的任务日志会以每分钟一次的频率异步同步至报表中；任务报表仅读取报表数据，极大提升加载速度；&#x000A;- 3、 Cron在线生成工具：任务新增、编辑框通过组件在线生成Cron表达式；&#x000A;- 4、 Cron下次执行时间查询：支持通过界面在线查看后续连续5次执行时间；&#x000A;- 5、 调度中心新增应用健康检查功能，借助“spring-boot-starter-actuator”，相对地址 “/actuator/health”；&#x000A;- 6、 DB脚本默认编码改为utf8mb4，修复字符乱码问题(建议Mysql版本5.7+)；&#x000A;- 7、 调度中心任务平均分配，触发组件每次获取与线程池数量相关数量的任务，避免大量任务集中在单个调度中心集群节点；&#x000A;- 8、 任务触发组件优化，预加载频率正常1s一次，当预加载轮空时主动休眠一个加载周期，动态降低加载频率从而降低DB压力；&#x000A;- 9、 调度组件优化：针对永远不会触发的Cron禁止配置和启动；任务Cron最后一次触发后再也不会触发时，比如一次性任务，主动停止相关任务；&#x000A;- 10、DB重连优化，修复DB宕机重连后任务调度停止的问题，重连后自动加入调度集群触发任务调度；&#x000A;- 11、注册监控线程优化，降低死锁几率；&#x000A;- 12、调度中心日志删除优化，改为分页获取ID并根据ID删除的方式，避免批量删除海量日志导致死锁问题；&#x000A;- 13、任务重试时参数丢失的问题修复；&#x000A;- 14、调度中心移除SQL中的 &quot;now()&quot; 函数；集群部署时不再依赖DB时钟，仅需要保证调度中心应用节点时钟一致即可；&#x000A;- 15、任务触发组件加载顺序调整，避免小概率情况下组件随机加载顺序导致的I18N的NPE问题;&#x000A;- 16、JobThread自销毁优化，避免并发触发导致triggerQueue中任务丢失问题；&#x000A;- 17、调度中心密码限制18位，修复修改密码超过18位无法登录的问题；&#x000A;- 18、任务告警组件分页参数无效问题修复；&#x000A;- 19、升级xxl-rpc版本：服务端线程优化，降低线程内存开销；IpUtil优化：增加连通性校，过滤明确非法的网卡；&#x000A;- 20、调度中心回调API服务改为restful方式；&#x000A;- 21、UI优化，任务列表和日志列表数据表格宽度比例调整，避免数据换行提升体验；&#x000A;- 22、登录界面取消默认填写的登录账号密码；&#x000A;- 23、执行器表属性调整，&quot;顺序&quot; 属性调整为整型，解决执行器数据较多时无法正确排序的问题；&#x000A;- 24、任务列表交互优化，支持查看任务所属执行器的注册节点；&#x000A;- 25、项目依赖升级至较新稳定版本，如spring、spring-boot、mybatis、slf4j、groovy等等；&#x000A;- 26、日志组件优化：调度中心支持控制每次请求最大加载行数，日志量太大时分批请求，避免单次加载日志量太大阻塞页面；&#x000A;&#x000A;### 7.29 版本 v2.1.2 Release Notes[2019-12-12]&#x000A;- 1、方法任务支持：由原来基于JobHandler类任务开发方式，优化为支持基于方法的任务开发方式；因此，可以支持单个类中开发多个任务方法，进行类复用&#x000A;```&#x000A;@XxlJob(&quot;demoJobHandler&quot;)&#x000A;public ReturnT&lt;String&gt; execute(String param) {&#x000A;    XxlJobLogger.log(&quot;hello world&quot;);&#x000A;    return ReturnT.SUCCESS;&#x000A;}&#x000A;```&#x000A;- 2、移除commons-exec，采用原生方式实现，降低第三方依赖；&#x000A;- 3、执行器回调乱码问题修复；&#x000A;- 4、调度中心dispatcher servlet加载顺序优化；&#x000A;- 5、执行器回调地址https兼容支持；&#x000A;- 6、多个项目依赖升级至较新稳定版本；&#x000A;- 注意：最新版本 &quot;XxlJobSpringExecutor&quot; 逻辑有调整，历史项目中该组件的配置方式请参考Sample示例项目进行调整，尤其注意需要移除组件的init和destroy方法；&#x000A;&#x000A;### 7.30 版本 v2.2.0 Release Notes[2020-04-14]&#x000A;- 1、RESTful API：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。&#x000A;- 2、任务复制功能：点击复制是弹出新建任务弹框，并初始化被复制任务信息；&#x000A;- 3、任务手动执行一次的时候，支持指定本次执行的机器地址，为空则从执行器获取；&#x000A;- 4、任务结果丢失处理：调度记录停留在 &quot;运行中&quot; 状态超过10min，且对应执行器心跳注册失败不在线，则将本地调度主动标记失败；&#x000A;- 5、调度中心升级springboot2.x；因此，系统要求JDK8+；&#x000A;- 6、XxlJob注解扫描方式优化，支持查找父类以及接口和基于类代理等常见情况；修复任务为空时小概率NPE问题；&#x000A;- 7、移除旧类注解JobHandler，推荐使用基于方法注解 &quot;@XxlJob&quot; 的方式进行任务开发；(如需保留类注解JobHandler使用方式，可以参考旧版逻辑定制开发);&#x000A;- 8、任务告警组件模块化：如果需要新增一种告警方式，只需要新增一个实现 &quot;com.xxl.job.admin.core.alarm.JobAlarm&quot; 接口的告警实现即可，更加灵活、方便定制；&#x000A;- 9、调度中心国际化完善：新增 &quot;中文繁体&quot; 支持。默认为 &quot;zh_CN&quot;/中文简体, 可选范围为 &quot;zh_CN&quot;/中文简体, &quot;zh_TC&quot;/中文繁体 and &quot;en&quot;/英文；&#x000A;- 10、执行器注册逻辑优化：新增配置项 ”注册地址 / xxl.job.executor.address“，优先使用该配置作为注册地址，为空时使用内嵌服务 ”IP:PORT“ 作为注册地址。从而更灵活的支持容器类型执行器动态IP和动态映射端口问题。&#x000A;- 11、默认数据库连接池调整为hikari，移除tomcat-jdbc依赖；&#x000A;- 12、多个项目依赖升级至较新稳定版本，如mybatis、groovy和mysql驱动等；&#x000A;- 13、执行器优雅停机优化，修复任务线程中断未join导致回调丢失的问题；&#x000A;- 14、一致性哈希路由策略优化：默认虚拟节点数量调整为100，提高路由的均衡性；&#x000A;- 15、通用HTTP任务Handler（httpJobHandler）优化，扩展自定义参数信息，示例参数如下；&#x000A;```&#x000A;url: http://www.xxx.com&#x000A;method: get 或 post&#x000A;data: post-data&#x000A;```&#x000A;- 16、SQL脚本编码默认utf8mb4执行，避免小概率下容器环境中乱码问题；&#x000A;- 17、Web IDE交互问题修复：输入源码备注之后按回车跳转error问题处理；&#x000A;- 18、执行器初始化逻辑优化：修复懒加载的Bean被提前初始化问题；&#x000A;- 19、执行器注册默认值优化；&#x000A;- 20、修复bootstrap.min.css.map 404问题；&#x000A;- 21、执行器UI交互优化,移除冗余order属性；&#x000A;- 22、执行备注消息长度限制，修复数据超长无法存储导致导致回调失败的问题；&#x000A;注意：XxlJobSpringExecutor组件个别字段调整：“appName” 调整为 “appname” ，升级时该组件时需要注意；   &#x000A;&#x000A;### 7.31 版本 v2.3.0 Release Notes[2021-02-09]&#x000A;- 1、【新增】调度过期策略：调度中心错过调度时间的补偿处理策略，包括：忽略、立即补偿触发一次等；&#x000A;- 2、【新增】触发策略：除了常规Cron、API、父子任务触发方式外，新增提供 &quot;固定间隔触发、（固定延时触发，实验中）&quot; 新触发方式；&#x000A;- 3、【新增】新增任务辅助工具 &quot;XxlJobHelper&quot;：提供统一任务辅助能力，包括：任务上下文信息维护获取（任务参数、任务ID、分片参数）、日志输出、任务结果设置……等；&#x000A;    - 3.1、&quot;ShardingUtil&quot; 组件废弃：改用 &quot;XxlJobHelper.getShardIndex()/getShardTotal();&quot; 获取分片参数；&#x000A;    - 3.2、&quot;XxlJobLogger&quot; 组件废弃：改用 &quot;XxlJobHelper.log&quot; 进行日志输出；&#x000A;- 4、【优化】任务核心类 &quot;IJobHandler&quot; 的 &quot;execute&quot; 方法取消出入参设计。改为通过 &quot;XxlJobHelper.getJobParam&quot; 获取任务参数并替代方法入参，通过 &quot;XxlJobHelper.handleSuccess/handleFail&quot; 设置任务结果并替代方法出参，示例代码如下；&#x000A;```&#x000A;@XxlJob(&quot;demoJobHandler&quot;)&#x000A;public void execute() {&#x000A;  String param = XxlJobHelper.getJobParam();    // 获取参数&#x000A;  XxlJobHelper.handleSuccess();                 // 设置任务结果&#x000A;}&#x000A;``` &#x000A;- 5、【优化】Cron编辑器增强：Cron编辑器修改cron时可实时查看最近运行时间;&#x000A;- 6、【优化】执行器示例项目规范整理；&#x000A;- 7、【优化】任务调度生命周期重构：调度（schedule）、触发(trigger)、执行（handle）、回调(callback)、结束（complete）；&#x000A;- 8、【优化】执行器注册组件优化：注册逻辑调整为异步方式，提高注册性能；&#x000A;- 9、【优化】执行器鉴权校验：执行器启动时主动校验accessToken，为空则主动Warn告警；（已规划安全强化：AccessToken动态生成、动态启停等）&#x000A;- 10、【优化】邮箱告警配置优化：将&quot;spring.mail.from&quot;与&quot;spring.mail.username&quot;属性拆分开，更加灵活的支持一些无密码邮箱服务；&#x000A;- 11、【优化】多个项目依赖升级至较新稳定版本，如netty、groovy、spring、springboot、mybatis等；&#x000A;- 12、【优化】UI组件常规升级，提升组件稳定性；&#x000A;- 13、【优化】调度中心页面交互优化：用户管理模块密码列取消；多处表达autocomplete取消；执行器管理模块XSS拦截校验等；&#x000A;- 14、【优化】调度中心任务状态探测慢SQL问题优化；&#x000A;- 15、【修复】GLUE-Java模式任务，init/destroy无法执行问题修复；&#x000A;- 16、【修复】Cron编辑器问题修复：修复小概率情况下cron单个字段修改时导致其他字段被重置问题；&#x000A;- 17、【修复】通用HTTP任务Handler（httpJobHandler）优化：修复 &quot;setDoOutput(true)&quot; 导致任务请求GetMethod失效问题；&#x000A;- 18、【修复】执行器Commandhandler示例任务优化，修复极端情况下脚本进程挂起问题；&#x000A;- 19、【修复】调度通讯组件优化，修复RestFul方式调用 DotNet 版本执行器时心跳检测失败问题；&#x000A;- 20、【修复】调度中心远程执行日志查询乱码问题修复；&#x000A;- 21、【修复】调度中心组件加载顺序优化，修复极端情况下调度组件初始慢导致的调度失败问题；&#x000A;- 22、【修复】执行器注册线程优化，修复极端情况下初始化失败时导致NPE问题；&#x000A;- 23、【修复】调度线程连接池优化，修复连接有效性校验超时问题；&#x000A;- 24、【修复】执行器注册表字段优化，解决执行器注册节点过多导致注册信息存储和更新失败的问题；&#x000A;- 25、【修复】轮训路由策略优化，修复小概率下并发问题；&#x000A;- 26、【修复】页面redirect跳转后https变为http问题修复；&#x000A;- 27、【修复】执行器日志清理优化，修复小概率下日志文件为空导致清理异常问题；      &#x000A;&#x000A;### 7.32 版本 v2.3.1 Release Notes[2022-05-21]&#x000A;- 1、【修复】修复风险漏洞，升级问题低版本项目依赖：CVE-2021-2471、CVE-2022-22965等。&#x000A;- 2、【修复】修复故障告警逻辑，邮箱校验逻辑下放至EmailJobAlarm中，避免对其他告警方式的干扰。&#x000A;- 3、【优化】调度通讯默认启用accessToken，提升系统安全性（建议生产环境自定义accessToken）。&#x000A;- 4、【优化】合并多项PR，项目代码结构、健壮性优化：PR-2833、PR-2812、PR-2541、PR-2537、PR-2514、PR-2509、PR-2591。&#x000A;- 5、【优化】任务线程名优化，提升可读性与问题定位效率(ISSUE-2527)。&#x000A;&#x000A;### 7.33 版本 v2.4.0 Release Notes[规划中]&#x000A;- 1、【优化】[规划中]任务日志重构：一次调度只记录一条主任务，维护起止时间和状态。&#x000A;    - 普通任务：只记录一条主任务；&#x000A;    - 广播任务：记录一条主任务，每个分片任务记录一条次任务，关联在主任务上；&#x000A;    - 重试任务：失败时，新增主任务。所有调度记录，包括入口调度和重试调度，均挂载主任务上。&#x000A;- 2、【优化】[规划中]分片任务：全部完成后才会出发后置节点；&#x000A;&#x000A;### 7.34 版本 v2.4.1 Release Notes[规划中]&#x000A;- 1、[规划中]DAG流程任务&#x000A;    - DAG任务：支持参数传递，共享数据：DAG任务创建、管理，DAG任务日志查看、操作；&#x000A;    - 子任务：废弃&#x000A;- 2、[规划中]多数据库支持，DAO层通过JPA实现，不限制数据库类型；&#x000A;- 3、[规划中]告警增强：邮件告警 + webhook告警；&#x000A;- 4、[规划中]安全强化：AccessToken动态生成、动态启停；控制调度、回调；&#x000A;- 5、[规划中]任务导入导出工具，灵活支持版本升级、迁移等场景。&#x000A;&#x000A;### TODO LIST&#x000A;- 1、任务分片路由：分片采用一致性Hash算法计算出尽量稳定的分片顺序，即使注册机器存在波动也不会引起分批分片顺序大的波动；目前采用IP自然排序，可以满足需求，待定；&#x000A;- 2、调度隔离：调度中心针对不同执行器，各自维护不同的调度和远程触发组件。&#x000A;- 3、调度任务优先级；&#x000A;- 4、多数据库支持，DAO层通过JPA实现，不限制数据库类型；&#x000A;- 5、执行器Log清理功能：调度中心Log删除时同步删除执行器中的Log文件；&#x000A;- 6、延时任务：API触发，支持&quot;动态传参、延时消费&quot;；该功能与 XXL-MQ 冲突，该场景建议用后者；&#x000A;- 7、调度线程池改为协程方式实现，大幅降低系统内存消耗；&#x000A;- 8、任务、执行器数据全量本地缓存；新增消息表广播通知；&#x000A;- 9、忙碌转移优化，全部机器忙碌时不再直接失败；&#x000A;- 10、任务触发参数优化：支持选择 &quot;Cron触发&quot;、&quot;固定间隔时间触发&quot;、&quot;指定时间点触发&quot;、&quot;不选择&quot; 等；&#x000A;- 11、调度日志列表加上执行时长列，并支持排序；&#x000A;- 12、DAG流程任务：&#x000A;    - 替换子任务，支持参数传递，共享数据：&#x000A;    - 配置并列的&quot;a-b、b-c&quot;路径列表，构成串行、并行、dag任务流程，&quot;dagre-d3&quot;绘图；任务依赖，流程图，子任务+会签任务，各节点日志；支持根据成功、失败选择分支；&#x000A;    - 分片任务：全部完成后才会出发后置节点；&#x000A;- 13、日期过滤：支持多个时间段排除；&#x000A;- 14、告警增强：&#x000A;    - 邮件告警：支持自定义标题、模板格式；&#x000A;    - webhook告警：支持自定义告警URL、请求体格式；&#x000A;- 15、新增任务运行模式 &quot;GLUE模式(GO) &quot;，支持GO任务；&#x000A;- 16、GLUE 模式 Web Ide 版本对比功能；&#x000A;- 17、注册中心优化，实时性注册发现：心跳注册间隔10s，refresh失败则首次注册并立即更新注册信息，心跳类似；30s过期销毁；&#x000A;- 18、提供执行器Docker镜像；&#x000A;- 19、脚本任务，支持数据参数，新版本仅支持单参数不支持需要兼容；&#x000A;- 20、批量调度：调度请求入queue，调度线程批量获取调度请求并发起远程调度；提高线程效率；&#x000A;- 21、执行器端口复用，复用容器端口提供通讯服务；&#x000A;- 22、分片任务全部成功后触发子任务；&#x000A;- 23、新增执行器描述属性；任务名称属性；&#x000A;- 24、自定义失败重试时间间隔；&#x000A;- 25、任务标签：方便搜索；&#x000A;- 26、执行器：dag执行器，不需要注册机器；&#x000A;&#x000A;&#x000A;## 八、其他&#x000A;&#x000A;### 8.1 项目贡献&#x000A;欢迎参与项目贡献！比如提交PR修复一个bug，或者新建 [Issue](https://github.com/xuxueli/xxl-job/issues/) 讨论新特性或者变更。&#x000A;&#x000A;### 8.2 用户接入登记&#x000A;更多接入的公司，欢迎在 [登记地址](https://github.com/xuxueli/xxl-job/issues/1 ) 登记，登记仅仅为了产品推广。&#x000A;&#x000A;### 8.3 开源协议和版权&#x000A;产品开源免费，并且将持续提供免费的社区技术支持。个人或企业内部可自由的接入和使用。如有需要可邮件联系作者免费获取项目授权。&#x000A;&#x000A;- Licensed under the GNU General Public License (GPL) v3.&#x000A;- Copyright (c) 2015-present, xuxueli.&#x000A;&#x000A;---&#x000A;### 捐赠&#x000A;无论捐赠金额多少都足够表达您这份心意，非常感谢 ：）      [前往捐赠](https://www.xuxueli.com/page/donate.html )&#x000A;</textarea>
<a class="ui button" id="copy-text" href="#">一键复制</a>
<a class="ui button edit-blob" title="只有登陆后才可以编辑" href="/xuxueli0323/xxl-job/edit/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md">编辑</a>
<a class="ui button web-ide" target="_blank" href="/-/ide/project/xuxueli0323/xxl-job/edit/master/-/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md">Web IDE</a>
<a class="ui button edit-raw" target="_blank" href="/xuxueli0323/xxl-job/raw/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md">原始数据</a>
<a class="ui button edit-blame" href="/xuxueli0323/xxl-job/blame/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md">按行查看</a>
<a class="ui button edit-history" href="/xuxueli0323/xxl-job/commits/master/doc/XXL-JOB%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3.md">历史</a>
</div>
<script>
  "use strict";
  try {
    if((gon.wait_fork!=undefined && gon.wait_fork==true) || (gon.wait_fetch!=undefined && gon.wait_fetch==true)){
      $('.edit-blob').popup({content:"当前仓库正在后台处理中,暂时无法编辑", on: 'hover', delay: { show: 200, hide: 200 }});
      $('.edit-blob').click(function(e){
        e.preventDefault();
      })
    }
  
    var setUrl = function() {
      var params = window.location.search
      if (params==undefined || $.trim(params).length==0) return;
      $('span.options').children('.basic').find('a').each(function(index,ele){
        var origin_href = $(ele).attr('href');
        if (origin_href!="#" && origin_href.indexOf('?') == -1){
          $(ele).attr('href',origin_href+params);
        }
      });
    }
  
    setUrl();
  
    var clipboard = null,
        $btncopy  = $("#copy-text");
  
    clipboard = new Clipboard("#copy-text", {
      text: function(trigger) {
        return $("#blob_raw").val();
      }
    })
  
    clipboard.on('success', function(e) {
      $btncopy.popup('hide');
      $btncopy.popup('destroy');
      $btncopy.popup({content: '已复制', position: 'bottom center'});
      $btncopy.popup('show');
    })
  
    clipboard.on('error', function(e) {
      var giteeModal = new GiteeModalHelper({okText: '确定'});
      giteeModal.alert("一键复制", '复制失败，请手动复制');
    })
  
    $(function() {
      $btncopy.popup({
        content: '点击复制',
        position: 'bottom center'
      })
    })
  
  } catch (error) {
    console.log('blob/action error:' + error);
  }
  
  $('.disabled-edit-readonly').popup({
    content: "只读文件不可编辑",
    className: {
      popup: 'ui popup',
    },
    position: 'bottom center',
  })
  $('.disabled-edit-readonly, .disabled-edit-status').click(function() {
    return false
  })
  $('.has_tooltip').popup({
    position: 'top center'
  });
</script>
<style>
  .disabled-edit-readonly, .disabled-edit-status {
    background-color: #dcddde !important;
    color: rgba(0, 0, 0, 0.4) !important;
    opacity: 0.3 !important;
    background-image: none !important;
    -webkit-box-shadow: none !important;
            box-shadow: none !important;
    cursor: default !important; }
  
  .drawio-iframe-code-card {
    position: relative; }
    .drawio-iframe-code-card textarea {
      width: 100%;
      height: 140px;
      resize: none; }
    .drawio-iframe-code-card .icon-clone {
      position: absolute;
      right: 32px;
      bottom: 32px; }
    .drawio-iframe-code-card iframe {
      border-radius: 2px;
      border: 1px solid #DEDEDF; }
</style>
</div>
</div>
<div class='blob-header-title mt-1 ubblock_tip'>
</div>
<div class='contributor-description'><span class='recent-commit' style='margin-top: 0.7rem'>
<a class="commit-author-link  js-popover-card " data-username="xuxueli0323" href="/xuxueli0323">许雪里</a>
<span>提交于</span>
<span class='timeago commit-date' title='2022-05-21 16:13:31 +0800'>
2022-05-21 16:13
</span>
.
<a href="/xuxueli0323/xxl-job/commit/76ab3f2cadb288df22a962af93caa54b1565fdac">update document</a>
</span>
</div>
</div>
<div class='clearfix'></div>
<div class='file_catalog'>
<div class='toggle'>
<i class='icon angle left'></i>
</div>
<div class='scroll-container'>
<div class='container'>
<div class='skeleton'>
<div class='line line1'></div>
<div class='line line2'></div>
<div class='line line3'></div>
<div class='line line1'></div>
<div class='line line2'></div>
<div class='line line3'></div>
</div>
</div>
</div>
</div>
<div class='file_content markdown-body'>
<h2>&#x000A;<a id="user-content-分布式任务调度平台xxl-job" class="anchor" href="#%E5%88%86%E5%B8%83%E5%BC%8F%E4%BB%BB%E5%8A%A1%E8%B0%83%E5%BA%A6%E5%B9%B3%E5%8F%B0xxl-job"></a>《分布式任务调度平台XXL-JOB》</h2>&#x000A;<p><a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Factions"><img src="https://github.com/xuxueli/xxl-job/workflows/Java%20CI/badge.svg" alt="Actions Status"></a>&#x000A;<a href="https://gitee.com/link?target=https%3A%2F%2Fmaven-badges.herokuapp.com%2Fmaven-central%2Fcom.xuxueli%2Fxxl-job%2F"><img src="https://maven-badges.herokuapp.com/maven-central/com.xuxueli/xxl-job/badge.svg" alt="Maven Central"></a>&#x000A;<a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Freleases"><img src="https://img.shields.io/github/release/xuxueli/xxl-job.svg" alt="GitHub release"></a>&#x000A;<a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2F"><img src="https://img.shields.io/github/stars/xuxueli/xxl-job" alt="GitHub stars"></a>&#x000A;<a href="https://gitee.com/link?target=https%3A%2F%2Fhub.docker.com%2Fr%2Fxuxueli%2Fxxl-job-admin%2F"><img src="https://img.shields.io/docker/pulls/xuxueli/xxl-job-admin" alt="Docker Status"></a>&#x000A;<a href="https://gitee.com/link?target=http%3A%2F%2Fwww.gnu.org%2Flicenses%2Fgpl-3.0.html"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License"></a>&#x000A;<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fpage%2Fdonate.html"><img src="https://img.shields.io/badge/%24-donate-ff69b4.svg?style=flat" alt="donate"></a></p>&#x000A;<p>[TOCM]</p>&#x000A;<p>[TOC]</p>&#x000A;<h2>&#x000A;<a id="user-content-一简介" class="anchor" href="#%E4%B8%80%E7%AE%80%E4%BB%8B"></a>一、简介</h2>&#x000A;<h3>&#x000A;<a id="user-content-11-概述" class="anchor" href="#11-%E6%A6%82%E8%BF%B0"></a>1.1 概述</h3>&#x000A;<p>XXL-JOB是一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。</p>&#x000A;<h3>&#x000A;<a id="user-content-12-社区交流" class="anchor" href="#12-%E7%A4%BE%E5%8C%BA%E4%BA%A4%E6%B5%81"></a>1.2 社区交流</h3>&#x000A;<ul>&#x000A;<li><a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fpage%2Fcommunity.html">社区交流</a></li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-13-特性" class="anchor" href="#13-%E7%89%B9%E6%80%A7"></a>1.3 特性</h3>&#x000A;<ul>&#x000A;<li>1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；</li>&#x000A;<li>2、动态：支持动态修改任务状态、启动/停止任务，以及终止运行中任务，即时生效；</li>&#x000A;<li>3、调度中心HA（中心式）：调度采用中心式设计，“调度中心”自研调度组件并支持集群部署，可保证调度中心HA；</li>&#x000A;<li>4、执行器HA（分布式）：任务分布式执行，任务"执行器"支持集群部署，可保证任务执行HA；</li>&#x000A;<li>5、注册中心: 执行器会周期性自动注册任务, 调度中心将会自动发现注册的任务并触发执行。同时，也支持手动录入执行器地址；</li>&#x000A;<li>6、弹性扩容缩容：一旦有新执行器机器上线或者下线，下次调度时将会重新分配任务；</li>&#x000A;<li>7、触发策略：提供丰富的任务触发策略，包括：Cron触发、固定间隔触发、固定延时触发、API（事件）触发、人工触发、父子任务触发；</li>&#x000A;<li>8、调度过期策略：调度中心错过调度时间的补偿处理策略，包括：忽略、立即补偿触发一次等；</li>&#x000A;<li>9、阻塞处理策略：调度过于密集执行器来不及处理时的处理策略，策略包括：单机串行（默认）、丢弃后续调度、覆盖之前调度；</li>&#x000A;<li>10、任务超时控制：支持自定义任务超时时间，任务运行超时将会主动中断任务；</li>&#x000A;<li>11、任务失败重试：支持自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；其中分片任务支持分片粒度的失败重试；</li>&#x000A;<li>12、任务失败告警；默认提供邮件方式失败告警，同时预留扩展接口，可方便的扩展短信、钉钉等告警方式；</li>&#x000A;<li>13、路由策略：执行器集群部署时提供丰富的路由策略，包括：第一个、最后一个、轮询、随机、一致性HASH、最不经常使用、最近最久未使用、故障转移、忙碌转移等；</li>&#x000A;<li>14、分片广播任务：执行器集群部署时，任务路由策略选择"分片广播"情况下，一次任务调度将会广播触发集群中所有执行器执行一次任务，可根据分片参数开发分片任务；</li>&#x000A;<li>15、动态分片：分片广播任务以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。</li>&#x000A;<li>16、故障转移：任务路由策略选择"故障转移"情况下，如果执行器集群中某一台机器故障，将会自动Failover切换到一台正常的执行器发送调度请求。</li>&#x000A;<li>17、任务进度监控：支持实时监控任务进度；</li>&#x000A;<li>18、Rolling实时日志：支持在线查看调度结果，并且支持以Rolling方式实时查看执行器输出的完整的执行日志；</li>&#x000A;<li>19、GLUE：提供Web IDE，支持在线开发任务逻辑代码，动态发布，实时编译生效，省略部署上线的过程。支持30个版本的历史版本回溯。</li>&#x000A;<li>20、脚本任务：支持以GLUE模式开发和运行脚本任务，包括Shell、Python、NodeJS、PHP、PowerShell等类型脚本;</li>&#x000A;<li>21、命令行任务：原生提供通用命令行任务Handler（Bean任务，"CommandJobHandler"）；业务方只需要提供命令行即可；</li>&#x000A;<li>22、任务依赖：支持配置子任务依赖，当父任务执行结束且执行成功后将会主动触发一次子任务的执行, 多个子任务用逗号分隔；</li>&#x000A;<li>23、一致性：“调度中心”通过DB锁保证集群分布式调度的一致性, 一次任务调度只会触发一次执行；</li>&#x000A;<li>24、自定义任务参数：支持在线配置调度任务入参，即时生效；</li>&#x000A;<li>25、调度线程池：调度系统多线程触发调度运行，确保调度精确执行，不被堵塞；</li>&#x000A;<li>26、数据加密：调度中心和执行器之间的通讯进行数据加密，提升调度信息安全性；</li>&#x000A;<li>27、邮件报警：任务失败时支持邮件报警，支持配置多邮件地址群发报警邮件；</li>&#x000A;<li>28、推送maven中央仓库: 将会把最新稳定版推送到maven中央仓库, 方便用户接入和使用;</li>&#x000A;<li>29、运行报表：支持实时查看运行数据，如任务数量、调度次数、执行器数量等；以及调度报表，如调度日期分布图，调度成功分布图等；</li>&#x000A;<li>30、全异步：任务调度流程全异步化设计实现，如异步调度、异步运行、异步回调等，有效对密集调度进行流量削峰，理论上支持任意时长任务的运行；</li>&#x000A;<li>31、跨语言：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。除此之外，还提供了 “多任务模式”和“httpJobHandler”等其他跨语言方案；</li>&#x000A;<li>32、国际化：调度中心支持国际化设置，提供中文、英文两种可选语言，默认为中文；</li>&#x000A;<li>33、容器化：提供官方docker镜像，并实时更新推送dockerhub，进一步实现产品开箱即用；</li>&#x000A;<li>34、线程池隔离：调度线程池进行隔离拆分，慢任务自动降级进入"Slow"线程池，避免耗尽调度线程，提高系统稳定性；</li>&#x000A;<li>35、用户管理：支持在线管理系统用户，存在管理员、普通用户两种角色；</li>&#x000A;<li>36、权限控制：执行器维度进行权限控制，管理员拥有全量权限，普通用户需要分配执行器权限后才允许相关操作；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-14-发展" class="anchor" href="#14-%E5%8F%91%E5%B1%95"></a>1.4 发展</h3>&#x000A;<p>于2015年中，我在github上创建XXL-JOB项目仓库并提交第一个commit，随之进行系统结构设计，UI选型，交互设计……</p>&#x000A;<p>于2015-11月，XXL-JOB终于RELEASE了第一个大版本V1.0， 随后我将之发布到OSCHINA，XXL-JOB在OSCHINA上获得了@红薯的热门推荐，同期分别达到了OSCHINA的“热门动弹”排行第一和git.oschina的开源软件月热度排行第一，在此特别感谢红薯，感谢大家的关注和支持。</p>&#x000A;<p>于2015-12月，我将XXL-JOB发表到我司内部知识库，并且得到内部同事认可。</p>&#x000A;<p>于2016-01月，我司展开XXL-JOB的内部接入和定制工作，在此感谢袁某和尹某两位同事的贡献，同时也感谢内部其他给与关注与支持的同事。</p>&#x000A;<p>于2017-05-13，在上海举办的 "<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fevent%2F2236961">第62期开源中国源创会</a>" 的 "放码过来" 环节，我登台对XXL-JOB做了演讲，台下五百位在场观众反响热烈（<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fquestion%2F2686220_2242120">图文回顾</a> ）。</p>&#x000A;<p>于2017-10-22，又拍云 Open Talk 联合 Spring Cloud 中国社区举办的 "<a href="https://gitee.com/link?target=https%3A%2F%2Fopentalk.upyun.com%2F303.html">进击的微服务实战派上海站</a>"，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。</p>&#x000A;<p>于2017-12-11，XXL-JOB有幸参会《<a href="https://gitee.com/link?target=http%3A%2F%2Fbj2017.archsummit.com%2F">InfoQ ArchSummit全球架构师峰会</a>》，并被拍拍贷架构总监"杨波老师"在专题 "<a href="https://gitee.com/link?target=http%3A%2F%2Fbj2017.archsummit.com%2Ftraining%2F2">微服务原理、基础架构和开源实践</a>" 中现场介绍。</p>&#x000A;<p>于2017-12-18，XXL-JOB参与"<a href="https://gitee.com/link?target=http%3A%2F%2Fwww.oschina.net%2Fproject%2Ftop_cn_2017%3Fsort%3D1">2017年度最受欢迎中国开源软件</a>"评比，在当时已录入的约九千个国产开源项目中角逐，最终进入了前30强。</p>&#x000A;<p>于2018-01-15，XXL-JOB参与"<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fnews%2F92438%2F2017-mayun-top-50">2017码云最火开源项目</a>"评比，在当时已录入的约六千五百个码云项目中角逐，最终进去了前20强。</p>&#x000A;<p>于2018-04-14，iTechPlus在上海举办的 "<a href="https://gitee.com/link?target=http%3A%2F%2Fwww.itdks.com%2Feventlist%2Fdetail%2F2065">2018互联网开发者大会</a>"，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。</p>&#x000A;<p>于2018-05-27，在上海举办的 "<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fevent%2F2278742">第75期开源中国源创会</a>" 的 "架构" 主题专场，我登台进行“基础架构与中间件图谱”主题演讲，台下上千位在场观众反响热烈（<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fquestion%2F3802184_2280606">图文回顾</a> ）。</p>&#x000A;<p>于2018-12-05，XXL-JOB参与"<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fproject%2Ftop_cn_2018%3Fsort%3D1">2018年度最受欢迎中国开源软件</a>"评比，在当时已录入的一万多个开源项目中角逐，最终排名第19名。</p>&#x000A;<p>于2019-12-10，XXL-JOB参与"<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fproject%2Ftop_cn_2019">2019年度最受欢迎中国开源软件</a>"评比，在当时已录入的一万多个开源项目中角逐，最终排名"开发框架和基础组件类"第9名。</p>&#x000A;<p>于2020-11-16，XXL-JOB参与"<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fproject%2Ftop_cn_2020">2020年度最受欢迎中国开源软件</a>"评比，在当时已录入的一万多个开源项目中角逐，最终排名"开发框架和基础组件类"第8名。</p>&#x000A;<p>于2021-12-06，XXL-JOB参与"<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.oschina.net%2Fproject%2Ftop_cn_2021">2021年度OSC中国开源项目评选</a> "评比，在当时已录入的一万多个开源项目中角逐，最终当选"最受欢迎项目"。</p>&#x000A;<blockquote>&#x000A;<p>我司大众点评目前已接入XXL-JOB，内部别名《Ferrari》（Ferrari基于XXL-JOB的V1.1版本定制而成，新接入应用推荐升级最新版本）。&#x000A;据最新统计, 自2016-01-21接入至2017-12-01期间，该系统已调度约100万次，表现优异。新接入应用推荐使用最新版本，因为经过数十个版本的更新，系统的任务模型、UI交互模型以及底层调度通讯模型都有了较大的优化和提升，核心功能更加稳定高效。</p>&#x000A;</blockquote>&#x000A;<p>至今，XXL-JOB已接入多家公司的线上产品线，接入场景如电商业务，O2O业务和大数据作业等，截止最新统计时间为止，XXL-JOB已接入的公司包括不限于：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">- 1、大众点评【美团点评】</span>&#x000A;<span id="LC2" class="line">- 2、山东学而网络科技有限公司；</span>&#x000A;<span id="LC3" class="line">- 3、安徽慧通互联科技有限公司；</span>&#x000A;<span id="LC4" class="line">- 4、人人聚财金服；</span>&#x000A;<span id="LC5" class="line">- 5、上海棠棣信息科技股份有限公司</span>&#x000A;<span id="LC6" class="line">- 6、运满满【运满满】</span>&#x000A;<span id="LC7" class="line">- 7、米其林 (中国区)【米其林】</span>&#x000A;<span id="LC8" class="line">- 8、妈妈联盟</span>&#x000A;<span id="LC9" class="line">- 9、九樱天下（北京）信息技术有限公司</span>&#x000A;<span id="LC10" class="line">- 10、万普拉斯科技有限公司【一加手机】</span>&#x000A;<span id="LC11" class="line">- 11、上海亿保健康管理有限公司</span>&#x000A;<span id="LC12" class="line">- 12、海尔馨厨【海尔】</span>&#x000A;<span id="LC13" class="line">- 13、河南大红包电子商务有限公司</span>&#x000A;<span id="LC14" class="line">- 14、成都顺点科技有限公司</span>&#x000A;<span id="LC15" class="line">- 15、深圳市怡亚通</span>&#x000A;<span id="LC16" class="line">- 16、深圳麦亚信科技股份有限公司</span>&#x000A;<span id="LC17" class="line">- 17、上海博莹科技信息技术有限公司</span>&#x000A;<span id="LC18" class="line">- 18、中国平安科技有限公司【中国平安】</span>&#x000A;<span id="LC19" class="line">- 19、杭州知时信息科技有限公司</span>&#x000A;<span id="LC20" class="line">- 20、博莹科技（上海）有限公司</span>&#x000A;<span id="LC21" class="line">- 21、成都依能股份有限责任公司</span>&#x000A;<span id="LC22" class="line">- 22、湖南高阳通联信息技术有限公司</span>&#x000A;<span id="LC23" class="line">- 23、深圳市邦德文化发展有限公司</span>&#x000A;<span id="LC24" class="line">- 24、福建阿思可网络教育有限公司</span>&#x000A;<span id="LC25" class="line">- 25、优信二手车【优信】</span>&#x000A;<span id="LC26" class="line">- 26、上海悠游堂投资发展股份有限公司【悠游堂】</span>&#x000A;<span id="LC27" class="line">- 27、北京粉笔蓝天科技有限公司</span>&#x000A;<span id="LC28" class="line">- 28、中秀科技(无锡)有限公司</span>&#x000A;<span id="LC29" class="line">- 29、武汉空心科技有限公司</span>&#x000A;<span id="LC30" class="line">- 30、北京蚂蚁风暴科技有限公司</span>&#x000A;<span id="LC31" class="line">- 31、四川互宜达科技有限公司</span>&#x000A;<span id="LC32" class="line">- 32、钱包行云（北京）科技有限公司</span>&#x000A;<span id="LC33" class="line">- 33、重庆欣才集团</span>&#x000A;<span id="LC34" class="line">- 34、咪咕互动娱乐有限公司【中国移动】</span>&#x000A;<span id="LC35" class="line">- 35、北京诺亦腾科技有限公司</span>&#x000A;<span id="LC36" class="line">- 36、增长引擎(北京)信息技术有限公司</span>&#x000A;<span id="LC37" class="line">- 37、北京英贝思科技有限公司</span>&#x000A;<span id="LC38" class="line">- 38、刚泰集团</span>&#x000A;<span id="LC39" class="line">- 39、深圳泰久信息系统股份有限公司</span>&#x000A;<span id="LC40" class="line">- 40、随行付支付有限公司</span>&#x000A;<span id="LC41" class="line">- 41、广州瀚农网络科技有限公司</span>&#x000A;<span id="LC42" class="line">- 42、享点科技有限公司</span>&#x000A;<span id="LC43" class="line">- 43、杭州比智科技有限公司</span>&#x000A;<span id="LC44" class="line">- 44、圳临界线网络科技有限公司</span>&#x000A;<span id="LC45" class="line">- 45、广州知识圈网络科技有限公司</span>&#x000A;<span id="LC46" class="line">- 46、国誉商业上海有限公司</span>&#x000A;<span id="LC47" class="line">- 47、海尔消费金融有限公司，嗨付、够花【海尔】</span>&#x000A;<span id="LC48" class="line">- 48、广州巴图鲁信息科技有限公司</span>&#x000A;<span id="LC49" class="line">- 49、深圳市鹏海运电子数据交换有限公司</span>&#x000A;<span id="LC50" class="line">- 50、深圳市亚飞电子商务有限公司</span>&#x000A;<span id="LC51" class="line">- 51、上海趣医网络有限公司</span>&#x000A;<span id="LC52" class="line">- 52、聚金资本</span>&#x000A;<span id="LC53" class="line">- 53、北京父母邦网络科技有限公司</span>&#x000A;<span id="LC54" class="line">- 54、中山元赫软件科技有限公司</span>&#x000A;<span id="LC55" class="line">- 55、中商惠民(北京)电子商务有限公司</span>&#x000A;<span id="LC56" class="line">- 56、凯京集团</span>&#x000A;<span id="LC57" class="line">- 57、华夏票联（北京）科技有限公司</span>&#x000A;<span id="LC58" class="line">- 58、拍拍贷【拍拍贷】</span>&#x000A;<span id="LC59" class="line">- 59、北京尚德机构在线教育有限公司</span>&#x000A;<span id="LC60" class="line">- 60、任子行股份有限公司</span>&#x000A;<span id="LC61" class="line">- 61、北京时态电子商务有限公司</span>&#x000A;<span id="LC62" class="line">- 62、深圳卷皮网络科技有限公司</span>&#x000A;<span id="LC63" class="line">- 63、北京安博通科技股份有限公司</span>&#x000A;<span id="LC64" class="line">- 64、未来无线网</span>&#x000A;<span id="LC65" class="line">- 65、厦门瓷禧网络有限公司</span>&#x000A;<span id="LC66" class="line">- 66、北京递蓝科软件股份有限公司</span>&#x000A;<span id="LC67" class="line">- 67、郑州创海软件科技公司</span>&#x000A;<span id="LC68" class="line">- 68、北京国槐信息科技有限公司</span>&#x000A;<span id="LC69" class="line">- 69、浪潮软件集团</span>&#x000A;<span id="LC70" class="line">- 70、多立恒(北京)信息技术有限公司</span>&#x000A;<span id="LC71" class="line">- 71、广州极迅客信息科技有限公司</span>&#x000A;<span id="LC72" class="line">- 72、赫基（中国）集团股份有限公司</span>&#x000A;<span id="LC73" class="line">- 73、海投汇</span>&#x000A;<span id="LC74" class="line">- 74、上海润益创业孵化器管理股份有限公司</span>&#x000A;<span id="LC75" class="line">- 75、汉纳森（厦门）数据股份有限公司</span>&#x000A;<span id="LC76" class="line">- 76、安信信托</span>&#x000A;<span id="LC77" class="line">- 77、岚儒财富</span>&#x000A;<span id="LC78" class="line">- 78、捷道软件</span>&#x000A;<span id="LC79" class="line">- 79、湖北享七网络科技有限公司</span>&#x000A;<span id="LC80" class="line">- 80、湖南创发科技责任有限公司</span>&#x000A;<span id="LC81" class="line">- 81、深圳小安时代互联网金融服务有限公司</span>&#x000A;<span id="LC82" class="line">- 82、湖北享七网络科技有限公司</span>&#x000A;<span id="LC83" class="line">- 83、钱包行云(北京)科技有限公司</span>&#x000A;<span id="LC84" class="line">- 84、360金融【360】</span>&#x000A;<span id="LC85" class="line">- 85、易企秀</span>&#x000A;<span id="LC86" class="line">- 86、摩贝（上海）生物科技有限公司</span>&#x000A;<span id="LC87" class="line">- 87、广东芯智慧科技有限公司</span>&#x000A;<span id="LC88" class="line">- 88、联想集团【联想】</span>&#x000A;<span id="LC89" class="line">- 89、怪兽充电</span>&#x000A;<span id="LC90" class="line">- 90、行圆汽车</span>&#x000A;<span id="LC91" class="line">- 91、深圳店店通科技邮箱公司</span>&#x000A;<span id="LC92" class="line">- 92、京东【京东】</span>&#x000A;<span id="LC93" class="line">- 93、米庄理财</span>&#x000A;<span id="LC94" class="line">- 94、咖啡易融</span>&#x000A;<span id="LC95" class="line">- 95、梧桐诚选</span>&#x000A;<span id="LC96" class="line">- 96、恒大地产【恒大】</span>&#x000A;<span id="LC97" class="line">- 97、昆明龙慧</span>&#x000A;<span id="LC98" class="line">- 98、上海涩瑶软件</span>&#x000A;<span id="LC99" class="line">- 99、易信【网易】</span>&#x000A;<span id="LC100" class="line">- 100、铜板街</span>&#x000A;<span id="LC101" class="line">- 101、杭州云若网络科技有限公司</span>&#x000A;<span id="LC102" class="line">- 102、特百惠（中国）有限公司</span>&#x000A;<span id="LC103" class="line">- 103、常山众卡运力供应链管理有限公司</span>&#x000A;<span id="LC104" class="line">- 104、深圳立创电子商务有限公司</span>&#x000A;<span id="LC105" class="line">- 105、杭州智诺科技股份有限公司</span>&#x000A;<span id="LC106" class="line">- 106、北京云漾信息科技有限公司</span>&#x000A;<span id="LC107" class="line">- 107、深圳市多银科技有限公司</span>&#x000A;<span id="LC108" class="line">- 108、亲宝宝</span>&#x000A;<span id="LC109" class="line">- 109、上海博卡软件科技有限公司</span>&#x000A;<span id="LC110" class="line">- 110、智慧树在线教育平台</span>&#x000A;<span id="LC111" class="line">- 111、米族金融</span>&#x000A;<span id="LC112" class="line">- 112、北京辰森世纪</span>&#x000A;<span id="LC113" class="line">- 113、云南滇医通</span>&#x000A;<span id="LC114" class="line">- 114、广州市分领网络科技有限责任公司</span>&#x000A;<span id="LC115" class="line">- 115、浙江微能科技有限公司</span>&#x000A;<span id="LC116" class="line">- 116、上海馨飞电子商务有限公司</span>&#x000A;<span id="LC117" class="line">- 117、上海宝尊电子商务有限公司</span>&#x000A;<span id="LC118" class="line">- 118、直客通科技技术有限公司</span>&#x000A;<span id="LC119" class="line">- 119、科度科技有限公司</span>&#x000A;<span id="LC120" class="line">- 120、上海数慧系统技术有限公司</span>&#x000A;<span id="LC121" class="line">- 121、我的医药网</span>&#x000A;<span id="LC122" class="line">- 122、多粉平台</span>&#x000A;<span id="LC123" class="line">- 123、铁甲二手机</span>&#x000A;<span id="LC124" class="line">- 124、上海海新得数据技术有限公司</span>&#x000A;<span id="LC125" class="line">- 125、深圳市珍爱网信息技术有限公司【珍爱网】</span>&#x000A;<span id="LC126" class="line">- 126、小蜜蜂</span>&#x000A;<span id="LC127" class="line">- 127、吉荣数科技</span>&#x000A;<span id="LC128" class="line">- 128、上海恺域信息科技有限公司</span>&#x000A;<span id="LC129" class="line">- 129、广州荔支网络有限公司【荔枝FM】</span>&#x000A;<span id="LC130" class="line">- 130、杭州闪宝科技有限公司</span>&#x000A;<span id="LC131" class="line">- 131、北京互联新网科技发展有限公司</span>&#x000A;<span id="LC132" class="line">- 132、誉道科技</span>&#x000A;<span id="LC133" class="line">- 133、山西兆盛房地产开发有限公司</span>&#x000A;<span id="LC134" class="line">- 134、北京蓝睿通达科技有限公司</span>&#x000A;<span id="LC135" class="line">- 135、月亮小屋（中国）有限公司【蓝月亮】</span>&#x000A;<span id="LC136" class="line">- 136、青岛国瑞信息技术有限公司</span>&#x000A;<span id="LC137" class="line">- 137、博雅云计算（北京）有限公司</span>&#x000A;<span id="LC138" class="line">- 138、华泰证券香港子公司</span>&#x000A;<span id="LC139" class="line">- 139、杭州东方通信软件技术有限公司</span>&#x000A;<span id="LC140" class="line">- 140、武汉博晟安全技术股份有限公司</span>&#x000A;<span id="LC141" class="line">- 141、深圳市六度人和科技有限公司</span>&#x000A;<span id="LC142" class="line">- 142、杭州趣维科技有限公司（小影）</span>&#x000A;<span id="LC143" class="line">- 143、宁波单车侠之家科技有限公司【单车侠】</span>&#x000A;<span id="LC144" class="line">- 144、丁丁云康信息科技（北京）有限公司</span>&#x000A;<span id="LC145" class="line">- 145、云钱袋</span>&#x000A;<span id="LC146" class="line">- 146、南京中兴力维</span>&#x000A;<span id="LC147" class="line">- 147、上海矽昌通信技术有限公司</span>&#x000A;<span id="LC148" class="line">- 148、深圳萨科科技</span>&#x000A;<span id="LC149" class="line">- 149、中通服创立科技有限责任公司</span>&#x000A;<span id="LC150" class="line">- 150、深圳市对庄科技有限公司</span>&#x000A;<span id="LC151" class="line">- 151、上证所信息网络有限公司</span>&#x000A;<span id="LC152" class="line">- 152、杭州火烧云科技有限公司【婚礼纪】</span>&#x000A;<span id="LC153" class="line">- 153、天津青芒果科技有限公司【芒果头条】</span>&#x000A;<span id="LC154" class="line">- 154、长飞光纤光缆股份有限公司</span>&#x000A;<span id="LC155" class="line">- 155、世纪凯歌（北京）医疗科技有限公司</span>&#x000A;<span id="LC156" class="line">- 156、浙江霖梓控股有限公司</span>&#x000A;<span id="LC157" class="line">- 157、江西腾飞网络技术有限公司</span>&#x000A;<span id="LC158" class="line">- 158、安迅物流有限公司</span>&#x000A;<span id="LC159" class="line">- 159、肉联网</span>&#x000A;<span id="LC160" class="line">- 160、北京北广梯影广告传媒有限公司</span>&#x000A;<span id="LC161" class="line">- 161、上海数慧系统技术有限公司</span>&#x000A;<span id="LC162" class="line">- 162、大志天成</span>&#x000A;<span id="LC163" class="line">- 163、上海云鹊医</span>&#x000A;<span id="LC164" class="line">- 164、上海云鹊医</span>&#x000A;<span id="LC165" class="line">- 165、墨迹天气【墨迹天气】</span>&#x000A;<span id="LC166" class="line">- 166、上海逸橙信息科技有限公司</span>&#x000A;<span id="LC167" class="line">- 167、沅朋物联</span>&#x000A;<span id="LC168" class="line">- 168、杭州恒生云融网络科技有限公司</span>&#x000A;<span id="LC169" class="line">- 169、绿米联创</span>&#x000A;<span id="LC170" class="line">- 170、重庆易宠科技有限公司</span>&#x000A;<span id="LC171" class="line">- 171、安徽引航科技有限公司（乐职网）</span>&#x000A;<span id="LC172" class="line">- 172、上海数联医信企业发展有限公司</span>&#x000A;<span id="LC173" class="line">- 173、良彬建材</span>&#x000A;<span id="LC174" class="line">- 174、杭州求是同创网络科技有限公司</span>&#x000A;<span id="LC175" class="line">- 175、荷马国际</span>&#x000A;<span id="LC176" class="line">- 176、点雇网</span>&#x000A;<span id="LC177" class="line">- 177、深圳市华星光电技术有限公司</span>&#x000A;<span id="LC178" class="line">- 178、厦门神州鹰软件科技有限公司</span>&#x000A;<span id="LC179" class="line">- 179、深圳市招商信诺人寿保险有限公司</span>&#x000A;<span id="LC180" class="line">- 180、上海好屋网信息技术有限公司</span>&#x000A;<span id="LC181" class="line">- 181、海信集团【海信】</span>&#x000A;<span id="LC182" class="line">- 182、信凌可信息科技（上海）有限公司</span>&#x000A;<span id="LC183" class="line">- 183、长春天成科技发展有限公司</span>&#x000A;<span id="LC184" class="line">- 184、用友金融信息技术股份有限公司【用友】</span>&#x000A;<span id="LC185" class="line">- 185、北京咖啡易融有限公司</span>&#x000A;<span id="LC186" class="line">- 186、国投瑞银基金管理有限公司</span>&#x000A;<span id="LC187" class="line">- 187、晋松(上海)网络信息技术有限公司</span>&#x000A;<span id="LC188" class="line">- 188、深圳市随手科技有限公司【随手记】</span>&#x000A;<span id="LC189" class="line">- 189、深圳水务科技有限公司</span>&#x000A;<span id="LC190" class="line">- 190、易企秀【易企秀】</span>&#x000A;<span id="LC191" class="line">- 191、北京磁云科技</span>&#x000A;<span id="LC192" class="line">- 192、南京蜂泰互联网科技有限公司</span>&#x000A;<span id="LC193" class="line">- 193、章鱼直播</span>&#x000A;<span id="LC194" class="line">- 194、奖多多科技</span>&#x000A;<span id="LC195" class="line">- 195、天津市神州商龙科技股份有限公司</span>&#x000A;<span id="LC196" class="line">- 196、岩心科技</span>&#x000A;<span id="LC197" class="line">- 197、车码科技（北京）有限公司</span>&#x000A;<span id="LC198" class="line">- 198、贵阳市投资控股集团</span>&#x000A;<span id="LC199" class="line">- 199、康旗股份</span>&#x000A;<span id="LC200" class="line">- 200、龙腾出行</span>&#x000A;<span id="LC201" class="line">- 201、杭州华量软件</span>&#x000A;<span id="LC202" class="line">- 202、合肥顶岭医疗科技有限公司</span>&#x000A;<span id="LC203" class="line">- 203、重庆表达式科技有限公司</span>&#x000A;<span id="LC204" class="line">- 204、上海米道信息科技有限公司</span>&#x000A;<span id="LC205" class="line">- 205、北京益友会科技有限公司</span>&#x000A;<span id="LC206" class="line">- 206、北京融贯电子商务有限公司</span>&#x000A;<span id="LC207" class="line">- 207、中国外汇交易中心</span>&#x000A;<span id="LC208" class="line">- 208、中国外运股份有限公司</span>&#x000A;<span id="LC209" class="line">- 209、中国上海晓圈教育科技有限公司</span>&#x000A;<span id="LC210" class="line">- 210、普联软件股份有限公司</span>&#x000A;<span id="LC211" class="line">- 211、北京科蓝软件股份有限公司</span>&#x000A;<span id="LC212" class="line">- 212、江苏斯诺物联科技有限公司</span>&#x000A;<span id="LC213" class="line">- 213、北京搜狐-狐友【搜狐】</span>&#x000A;<span id="LC214" class="line">- 214、新大陆网商金融</span>&#x000A;<span id="LC215" class="line">- 215、山东神码中税信息科技有限公司</span>&#x000A;<span id="LC216" class="line">- 216、河南汇顺网络科技有限公司</span>&#x000A;<span id="LC217" class="line">- 217、北京华夏思源科技发展有限公司</span>&#x000A;<span id="LC218" class="line">- 218、上海东普信息科技有限公司</span>&#x000A;<span id="LC219" class="line">- 219、上海鸣勃网络科技有限公司</span>&#x000A;<span id="LC220" class="line">- 220、广东学苑教育发展有限公司</span>&#x000A;<span id="LC221" class="line">- 221、深圳强时科技有限公司</span>&#x000A;<span id="LC222" class="line">- 222、上海云砺信息科技有限公司</span>&#x000A;<span id="LC223" class="line">- 223、重庆愉客行网络有限公司</span>&#x000A;<span id="LC224" class="line">- 224、数云</span>&#x000A;<span id="LC225" class="line">- 225、国家电网运检部</span>&#x000A;<span id="LC226" class="line">- 226、杭州找趣</span>&#x000A;<span id="LC227" class="line">- 227、浩鲸云计算科技股份有限公司</span>&#x000A;<span id="LC228" class="line">- 228、科大讯飞【科大讯飞】</span>&#x000A;<span id="LC229" class="line">- 229、杭州行装网络科技有限公司</span>&#x000A;<span id="LC230" class="line">- 230、即有分期金融</span>&#x000A;<span id="LC231" class="line">- 231、深圳法司德信息科技有限公司</span>&#x000A;<span id="LC232" class="line">- 232、上海博复信息科技有限公司</span>&#x000A;<span id="LC233" class="line">- 233、杭州云嘉云计算有限公司</span>&#x000A;<span id="LC234" class="line">- 234、有家民宿(有家美宿)</span>&#x000A;<span id="LC235" class="line">- 235、北京赢销通软件技术有限公司</span>&#x000A;<span id="LC236" class="line">- 236、浙江聚有财金融服务外包有限公司</span>&#x000A;<span id="LC237" class="line">- 237、易族智汇(北京)科技有限公司</span>&#x000A;<span id="LC238" class="line">- 238、合肥顶岭医疗科技开发有限公司</span>&#x000A;<span id="LC239" class="line">- 239、车船宝(深圳)旭珩科技有限公司)</span>&#x000A;<span id="LC240" class="line">- 240、广州富力地产有限公司</span>&#x000A;<span id="LC241" class="line">- 241、氢课（上海）教育科技有限公司</span>&#x000A;<span id="LC242" class="line">- 242、武汉氪细胞网络技术有限公司</span>&#x000A;<span id="LC243" class="line">- 243、杭州有云科技有限公司</span>&#x000A;<span id="LC244" class="line">- 244、上海仙豆智能机器人有限公司</span>&#x000A;<span id="LC245" class="line">- 245、拉卡拉支付股份有限公司【拉卡拉】</span>&#x000A;<span id="LC246" class="line">- 246、虎彩印艺股份有限公司</span>&#x000A;<span id="LC247" class="line">- 247、北京数微科技有限公司</span>&#x000A;<span id="LC248" class="line">- 248、广东智瑞科技有限公司</span>&#x000A;<span id="LC249" class="line">- 249、找钢网</span>&#x000A;<span id="LC250" class="line">- 250、九机网</span>&#x000A;<span id="LC251" class="line">- 251、杭州跑跑网络科技有限公司</span>&#x000A;<span id="LC252" class="line">- 252、深圳未来云集</span>&#x000A;<span id="LC253" class="line">- 253、杭州每日给力科技有限公司</span>&#x000A;<span id="LC254" class="line">- 254、上海齐犇信息科技有限公司</span>&#x000A;<span id="LC255" class="line">- 255、滴滴出行【滴滴】</span>&#x000A;<span id="LC256" class="line">- 256、合肥云诊信息科技有限公司</span>&#x000A;<span id="LC257" class="line">- 257、云知声智能科技股份有限公司</span>&#x000A;<span id="LC258" class="line">- 258、南京坦道科技有限公司</span>&#x000A;<span id="LC259" class="line">- 259、爱乐优（二手平台）</span>&#x000A;<span id="LC260" class="line">- 260、猫眼电影（私有化部署）【猫眼电影】</span>&#x000A;<span id="LC261" class="line">- 261、美团大象（私有化部署）【美团大象】</span>&#x000A;<span id="LC262" class="line">- 262、作业帮教育科技（北京）有限公司【作业帮】</span>&#x000A;<span id="LC263" class="line">- 263、北京小年糕互联网技术有限公司</span>&#x000A;<span id="LC264" class="line">- 264、山东矩阵软件工程股份有限公司</span>&#x000A;<span id="LC265" class="line">- 265、陕西国驿软件科技有限公司</span>&#x000A;<span id="LC266" class="line">- 266、君开信息科技</span>&#x000A;<span id="LC267" class="line">- 267、村鸟网络科技有限责任公司</span>&#x000A;<span id="LC268" class="line">- 268、云南国际信托有限公司</span>&#x000A;<span id="LC269" class="line">- 269、金智教育</span>&#x000A;<span id="LC270" class="line">- 270、珠海市筑巢科技有限公司</span>&#x000A;<span id="LC271" class="line">- 271、上海百胜软件股份有限公司</span>&#x000A;<span id="LC272" class="line">- 272、深圳市科盾科技有限公司</span>&#x000A;<span id="LC273" class="line">- 273、哈啰出行【哈啰】</span>&#x000A;<span id="LC274" class="line">- 274、途虎养车【途虎】</span>&#x000A;<span id="LC275" class="line">- 275、卡思优派人力资源集团</span>&#x000A;<span id="LC276" class="line">- 276、南京观为智慧软件科技有限公司</span>&#x000A;<span id="LC277" class="line">- 277、杭州城市大脑科技有限公司</span>&#x000A;<span id="LC278" class="line">- 278、猿辅导【猿辅导】</span>&#x000A;<span id="LC279" class="line">- 279、洛阳健创网络科技有限公司</span>&#x000A;<span id="LC280" class="line">- 280、魔力耳朵</span>&#x000A;<span id="LC281" class="line">- 281、亿阳信通</span>&#x000A;<span id="LC282" class="line">- 282、上海招鲤科技有限公司</span>&#x000A;<span id="LC283" class="line">- 283、四川商旅无忧科技服务有限公司</span>&#x000A;<span id="LC284" class="line">- 284、UU跑腿</span>&#x000A;<span id="LC285" class="line">- 285、北京老虎证券【老虎证券】</span>&#x000A;<span id="LC286" class="line">- 286、悠活省吧（北京）网络科技有限公司</span>&#x000A;<span id="LC287" class="line">- 287、F5未来商店</span>&#x000A;<span id="LC288" class="line">- 288、深圳环阳通信息技术有限公司</span>&#x000A;<span id="LC289" class="line">- 289、遠傳電信</span>&#x000A;<span id="LC290" class="line">- 290、作业帮（北京）教育科技有限公司【作业帮】</span>&#x000A;<span id="LC291" class="line">- 291、成都科鸿智信科技有限公司</span>&#x000A;<span id="LC292" class="line">- 292、北京木屋时代科技有限公司</span>&#x000A;<span id="LC293" class="line">- 293、大学通（哈尔滨）科技有限责任公司</span>&#x000A;<span id="LC294" class="line">- 294、浙江华坤道威数据科技有限公司</span>&#x000A;<span id="LC295" class="line">- 295、吉祥航空【吉祥航空】</span>&#x000A;<span id="LC296" class="line">- 296、南京圆周网络科技有限公司</span>&#x000A;<span id="LC297" class="line">- 297、广州市洋葱omall电子商务</span>&#x000A;<span id="LC298" class="line">- 298、天津联物科技有限公司</span>&#x000A;<span id="LC299" class="line">- 299、跑哪儿科技（北京）有限公司</span>&#x000A;<span id="LC300" class="line">- 300、深圳市美西西餐饮有限公司(喜茶)</span>&#x000A;<span id="LC301" class="line">- 301、平安不动产有限公司【平安】</span>&#x000A;<span id="LC302" class="line">- 302、江苏中海昇物联科技有限公司</span>&#x000A;<span id="LC303" class="line">- 303、湖南牙医帮科技有限公司</span>&#x000A;<span id="LC304" class="line">- 304、重庆民航凯亚信息技术有限公司（易通航）</span>&#x000A;<span id="LC305" class="line">- 305、递易（上海）智能科技有限公司</span>&#x000A;<span id="LC306" class="line">- 306、亚朵</span>&#x000A;<span id="LC307" class="line">- 307、浙江新课堂教育股份有限公司</span>&#x000A;<span id="LC308" class="line">- 308、北京蜂创科技有限公司</span>&#x000A;<span id="LC309" class="line">- 309、德一智慧城市信息系统有限公司</span>&#x000A;<span id="LC310" class="line">- 310、北京翼点科技有限公司</span>&#x000A;<span id="LC311" class="line">- 311、湖南智数新维度信息科技有限公司</span>&#x000A;<span id="LC312" class="line">- 312、北京玖扬博文文化发展有限公司</span>&#x000A;<span id="LC313" class="line">- 313、上海宇珩信息科技有限公司</span>&#x000A;<span id="LC314" class="line">- 314、全景智联（武汉）科技有限公司</span>&#x000A;<span id="LC315" class="line">- 315、天津易客满国际物流有限公司</span>&#x000A;<span id="LC316" class="line">- 316、南京爱福路汽车科技有限公司</span>&#x000A;<span id="LC317" class="line">- 317、我房旅居集团</span>&#x000A;<span id="LC318" class="line">- 318、湛江亲邻科技有限公司</span>&#x000A;<span id="LC319" class="line">- 319、深圳市姜科网络有限公司</span>&#x000A;<span id="LC320" class="line">- 320、青岛日日顺物流有限公司</span>&#x000A;<span id="LC321" class="line">- 321、南京太川信息技术有限公司</span>&#x000A;<span id="LC322" class="line">- 322、美图之家科技优先公司【美图】</span>&#x000A;<span id="LC323" class="line">- 323、南京太川信息技术有限公司</span>&#x000A;<span id="LC324" class="line">- 324、众薪科技（北京）有限公司</span>&#x000A;<span id="LC325" class="line">- 325、武汉安安物联科技有限公司</span>&#x000A;<span id="LC326" class="line">- 326、北京智客朗道网络科技有限公司</span>&#x000A;<span id="LC327" class="line">- 327、深圳市超级猩猩健身管理管理有限公司</span>&#x000A;<span id="LC328" class="line">- 328、重庆达志科技有限公司</span>&#x000A;<span id="LC329" class="line">- 329、上海享评信息科技有限公司</span>&#x000A;<span id="LC330" class="line">- 330、薪得付信息科技</span>&#x000A;<span id="LC331" class="line">- 331、跟谁学</span>&#x000A;<span id="LC332" class="line">- 332、中道（苏州）旅游网络科技有限公司</span>&#x000A;<span id="LC333" class="line">- 333、广州小卫科技有限公司</span>&#x000A;<span id="LC334" class="line">- 334、上海非码网络科技有限公司</span>&#x000A;<span id="LC335" class="line">- 335、途家网网络技术（北京）有限公司【途家】</span>&#x000A;<span id="LC336" class="line">- 336、广州辉凡信息科技有限公司</span>&#x000A;<span id="LC337" class="line">- 337、天维尔信息科技股份有限公司</span>&#x000A;<span id="LC338" class="line">- 338、上海极豆科技有限公司</span>&#x000A;<span id="LC339" class="line">- 339、苏州触达信息技术有限公司</span>&#x000A;<span id="LC340" class="line">- 340、北京热云科技有限公司</span>&#x000A;<span id="LC341" class="line">- 341、中智企服（北京）科技有限公司</span>&#x000A;<span id="LC342" class="line">- 342、易联云计算（杭州）有限责任公司</span>&#x000A;<span id="LC343" class="line">- 343、青岛航空股份有限公司【青岛航空】</span>&#x000A;<span id="LC344" class="line">- 344、山西博睿通科技有限公司</span>&#x000A;<span id="LC345" class="line">- 345、网易杭州网络有限公司【网易】</span>&#x000A;<span id="LC346" class="line">- 346、北京果果乐学科技有限公司</span>&#x000A;<span id="LC347" class="line">- 347、百望股份有限公司</span>&#x000A;<span id="LC348" class="line">- 348、中保金服（深圳）科技有限公司</span>&#x000A;<span id="LC349" class="line">- 349、天津运友物流科技股份有限公司</span>&#x000A;<span id="LC350" class="line">- 350、广东创能科技股份有限公司</span>&#x000A;<span id="LC351" class="line">- 351、上海倚博信息科技有限公司</span>&#x000A;<span id="LC352" class="line">- 352、深圳百果园实业（集团）股份有限公司</span>&#x000A;<span id="LC353" class="line">- 353、广州细刻网络科技有限公司</span>&#x000A;<span id="LC354" class="line">- 354、武汉鸿业众创科技有限公司</span>&#x000A;<span id="LC355" class="line">- 355、金锡科技（广州）有限公司</span>&#x000A;<span id="LC356" class="line">- 356、易瑞国际电子商务有限公司</span>&#x000A;<span id="LC357" class="line">- 357、奇点云</span>&#x000A;<span id="LC358" class="line">- 358、中视信息科技有限公司</span>&#x000A;<span id="LC359" class="line">- 359、开源项目:datax-web</span>&#x000A;<span id="LC360" class="line">- 360、云知声智能科技股份有限公司</span>&#x000A;<span id="LC361" class="line">- 361、开源项目:bboss</span>&#x000A;<span id="LC362" class="line">- 362、成都深驾科技有限公司</span>&#x000A;<span id="LC363" class="line">- 363、FunPlus【趣加】</span>&#x000A;<span id="LC364" class="line">- 364、杭州创匠信科技有限公司</span>&#x000A;<span id="LC365" class="line">- 365、龙匠（北京）科技发展有限公司</span>&#x000A;<span id="LC366" class="line">- 366、广州一链通互联网科技有限公司</span>&#x000A;<span id="LC367" class="line">- 367、上海星艾网络科技有限公司</span>&#x000A;<span id="LC368" class="line">- 368、虎博网络技术(上海)有限公司</span>&#x000A;<span id="LC369" class="line">- 369、青岛优米信息技术有限公司</span>&#x000A;<span id="LC370" class="line">- 370、八维通科技有限公司</span>&#x000A;<span id="LC371" class="line">- 371、烟台合享智星数据科技有限公司</span>&#x000A;<span id="LC372" class="line">- 372、东吴证券股份有限公司</span>&#x000A;<span id="LC373" class="line">- 373、中通云仓股份有限公司【中通】</span>&#x000A;<span id="LC374" class="line">- 374、北京加菲猫科技有限公司</span>&#x000A;<span id="LC375" class="line">- 375、北京匠心演绎科技有限公司</span>&#x000A;<span id="LC376" class="line">- 376、宝贝走天下</span>&#x000A;<span id="LC377" class="line">- 377、厦门众库科技有限公司</span>&#x000A;<span id="LC378" class="line">- 378、海通证券数据中心</span>&#x000A;<span id="LC379" class="line">- 389、湖南快乐通宝小额贷款有限公司</span>&#x000A;<span id="LC380" class="line">- 380、浙江大华技术股份有限公司</span>&#x000A;<span id="LC381" class="line">- 381、杭州魔筷科技有限公司</span>&#x000A;<span id="LC382" class="line">- 382、青岛掌讯通区块链科技有限公司</span>&#x000A;<span id="LC383" class="line">- 383、新大陆金融科技</span>&#x000A;<span id="LC384" class="line">- 384、常州玺拓软件科技有限公司</span>&#x000A;<span id="LC385" class="line">- 385、北京正保网格教育科技有限公司</span>&#x000A;<span id="LC386" class="line">- 386、统一企业（中国）投资有限公司【统一】</span>&#x000A;<span id="LC387" class="line">- 387、微革网络科技有限公司</span>&#x000A;<span id="LC388" class="line">- 388、杭州融易算科技有限公司</span>&#x000A;<span id="LC389" class="line">- 399、青岛上啥班网络科技有限公司</span>&#x000A;<span id="LC390" class="line">- 390、京东酒世界</span>&#x000A;<span id="LC391" class="line">- 391、杭州爱博仕科技有限公司</span>&#x000A;<span id="LC392" class="line">- 392、五星金服控股有限公司</span>&#x000A;<span id="LC393" class="line">- 393、福建乐摩物联科技有限公司</span>&#x000A;<span id="LC394" class="line">- 394、百炼智能科技有限公司</span>&#x000A;<span id="LC395" class="line">- 395、山东能源数智云科技有限公司</span>&#x000A;<span id="LC396" class="line">- 396、招商局能源运输股份有限公司</span>&#x000A;<span id="LC397" class="line">- 397、三一集团【三一】</span>&#x000A;<span id="LC398" class="line">- 398、东巴文（深圳）健康管理有限公司</span>&#x000A;<span id="LC399" class="line">- 399、索易软件</span>&#x000A;<span id="LC400" class="line">- 400、深圳市宁远科技有限公司</span>&#x000A;<span id="LC401" class="line">- 401、熙牛医疗</span>&#x000A;<span id="LC402" class="line">- 402、南京智鹤电子科技有限公司</span>&#x000A;<span id="LC403" class="line">- 403、嘀嗒出行【嘀嗒出行】</span>&#x000A;<span id="LC404" class="line">- 404、广州虎牙信息科技有限公司【虎牙】</span>&#x000A;<span id="LC405" class="line">- 405、广州欧莱雅百库网络科技有限公司【欧莱雅】</span>&#x000A;<span id="LC406" class="line">- 406、微微科技有限公司</span>&#x000A;<span id="LC407" class="line">- 407、我爱我家房地产经纪有限公司【我爱我家】</span>&#x000A;<span id="LC408" class="line">- 408、九号发现</span>&#x000A;<span id="LC409" class="line">- 409、薪人薪事</span>&#x000A;<span id="LC410" class="line">- 410、武汉氪细胞网络技术有限公司</span>&#x000A;<span id="LC411" class="line">- 411、广州市斯凯奇商业有限公司</span>&#x000A;<span id="LC412" class="line">- 412、微淼商学院</span>&#x000A;<span id="LC413" class="line">- 413、杭州车盛科技有限公司</span>&#x000A;<span id="LC414" class="line">- 414、深兰科技（上海）有限公司</span>&#x000A;<span id="LC415" class="line">- 415、安徽中科美络信息技术有限公司</span>&#x000A;<span id="LC416" class="line">- 416、比亚迪汽车工业有限公司【比亚迪】</span>&#x000A;<span id="LC417" class="line">- 417、湖南小桔信息技术有限公司</span>&#x000A;<span id="LC418" class="line">- 418、安徽科大国创软件科技有限公司</span>&#x000A;<span id="LC419" class="line">- 419、克而瑞</span>&#x000A;<span id="LC420" class="line">- 420、陕西云基华海信息技术有限公司</span>&#x000A;<span id="LC421" class="line">- 421、安徽深宁科技有限公司</span>&#x000A;<span id="LC422" class="line">- 422、广东康爱多数字健康有限公司</span>&#x000A;<span id="LC423" class="line">- 423、嘉里电子商务</span>&#x000A;<span id="LC424" class="line">- 424、上海时代光华教育发展有限公司</span>&#x000A;<span id="LC425" class="line">- 425、CityDo</span>&#x000A;<span id="LC426" class="line">- 426、上海禹知信息科技有限公司</span>&#x000A;<span id="LC427" class="line">- 427、广东智瑞科技有限公司</span>&#x000A;<span id="LC428" class="line">- 428、西安爱铭网络科技有限公司</span>&#x000A;<span id="LC429" class="line">- 429、心医国际数字医疗系统(大连)有限公司</span>&#x000A;<span id="LC430" class="line">- 430、乐其电商</span>&#x000A;<span id="LC431" class="line">- 431、锐达科技</span>&#x000A;<span id="LC432" class="line">- 432、天津长城滨银汽车金融有限公司</span>&#x000A;<span id="LC433" class="line">- 433、代码网</span>&#x000A;<span id="LC434" class="line">- 434、东莞市东城乔伦软件开发工作室</span>&#x000A;<span id="LC435" class="line">- 435、浙江百应科技有限公司</span>&#x000A;<span id="LC436" class="line">- 436、上海力爱帝信息技术有限公司(Red E)</span>&#x000A;<span id="LC437" class="line">- 437、云徙科技有限公司</span>&#x000A;<span id="LC438" class="line">- 438、北京康智乐思网络科技有限公司【大姨吗APP】</span>&#x000A;<span id="LC439" class="line">- 439、安徽开元瞬视科技有限公司</span>&#x000A;<span id="LC440" class="line">- 440、立方</span>&#x000A;<span id="LC441" class="line">- 441、厦门纵行科技</span>&#x000A;<span id="LC442" class="line">- 442、乐山-菲尼克斯半导体有限公司</span>&#x000A;<span id="LC443" class="line">- 443、武汉光谷联合集团有限公司</span>&#x000A;<span id="LC444" class="line">- 444、上海金仕达软件科技有限公司</span>&#x000A;<span id="LC445" class="line">- 445、深圳易世通达科技有限公司</span>&#x000A;<span id="LC446" class="line">- 446、爱动超越人工智能科技（北京）有限责任公司</span>&#x000A;<span id="LC447" class="line">- 447、迪普信（北京）科技有限公司</span>&#x000A;<span id="LC448" class="line">- 448、掌站科技（北京）有限公司</span>&#x000A;<span id="LC449" class="line">- 449、深圳市华云中盛股份有限公司</span>&#x000A;<span id="LC450" class="line">- 450、上海原圈科技有限公司</span>&#x000A;<span id="LC451" class="line">- 451、广州赞赏信息科技有限公司</span>&#x000A;<span id="LC452" class="line">- 452、Amber Group</span>&#x000A;<span id="LC453" class="line">- 453、德威国际货运代理（上海）公司</span>&#x000A;<span id="LC454" class="line">- 454、浙江杰夫兄弟智慧科技有限公司</span>&#x000A;<span id="LC455" class="line">- 455、信也科技</span>&#x000A;<span id="LC456" class="line">- 456、开思时代科技（深圳）有限公司</span>&#x000A;<span id="LC457" class="line">- 457、大连槐德科技有限公司</span>&#x000A;<span id="LC458" class="line">- 458、同程生活</span>&#x000A;<span id="LC459" class="line">- 459、松果出行</span>&#x000A;<span id="LC460" class="line">- 460、企鹅杏仁集团</span>&#x000A;<span id="LC461" class="line">- 461、宁波科云信息科技有限公司</span>&#x000A;<span id="LC462" class="line">- 462、上海格蓝威驰信息科技有限公司</span>&#x000A;<span id="LC463" class="line">- 463、杭州趣淘鲸科技有限公司</span>&#x000A;<span id="LC464" class="line">- 464、湖州市数字惠民科技有限公司</span>&#x000A;<span id="LC465" class="line">- 465、乐普（北京）医疗器械股份有限公司</span>&#x000A;<span id="LC466" class="line">- 466、广州市晴川高新技术开发有限公司</span>&#x000A;<span id="LC467" class="line">- 467、山西缇客科技有限公司</span>&#x000A;<span id="LC468" class="line">- 468、徐州卡西穆电子商务有限公司</span>&#x000A;<span id="LC469" class="line">- 469、格创东智科技有限公司</span>&#x000A;<span id="LC470" class="line">- 470、世纪龙信息网络有限责任公司</span>&#x000A;<span id="LC471" class="line">- 471、邦道科技有限公司</span>&#x000A;<span id="LC472" class="line">- 472、河南中盟新云科技股份有限公司</span>&#x000A;<span id="LC473" class="line">- 473、横琴人寿保险有限公司</span>&#x000A;<span id="LC474" class="line">- 474、上海海隆华钟信息技术有限公司</span>&#x000A;<span id="LC475" class="line">- 475、上海久湛</span>&#x000A;<span id="LC476" class="line">- 476、上海仙豆智能机器人有限公司</span>&#x000A;<span id="LC477" class="line">- 477、广州汇尚网络科技有限公司</span>&#x000A;<span id="LC478" class="line">- 478、深圳市阿卡索资讯股份有限公司</span>&#x000A;<span id="LC479" class="line">- 479、青岛佳家康健康管理有限责任公司</span>&#x000A;<span id="LC480" class="line">- 480、蓝城兄弟</span>&#x000A;<span id="LC481" class="line">- 481、成都天府通金融服务股份有限公司</span>&#x000A;<span id="LC482" class="line">- 482、深圳云镖网络科技有限公司</span>&#x000A;<span id="LC483" class="line">- 483、上海影创科技</span>&#x000A;<span id="LC484" class="line">- 484、成都艾拉物联</span>&#x000A;<span id="LC485" class="line">- 485、北京客邻尚品网络技术有限公司</span>&#x000A;<span id="LC486" class="line">- 486、IT实战联盟</span>&#x000A;<span id="LC487" class="line">- 487、杭州尤拉夫科技有限公司</span>&#x000A;<span id="LC488" class="line">- 488、中大检测(湖南)股份有限公司</span>&#x000A;<span id="LC489" class="line">- 489、江苏电老虎工业互联网股份有限公司</span>&#x000A;<span id="LC490" class="line">- 490、上海助通信息科技有限公司</span>&#x000A;<span id="LC491" class="line">- 491、北京符节科技有限公司</span>&#x000A;<span id="LC492" class="line">- 492、杭州英祐科技有限公司</span>&#x000A;<span id="LC493" class="line">- 493、江苏电老虎工业互联网股份有限公司</span>&#x000A;<span id="LC494" class="line">- 494、深圳市点猫科技有限公司</span>&#x000A;<span id="LC495" class="line">- 495、杭州天音</span>&#x000A;<span id="LC496" class="line">- 496、深圳市二十一科技互联网有限公司</span>&#x000A;<span id="LC497" class="line">- 497、海南海口翎度科技</span>&#x000A;<span id="LC498" class="line">- 498、北京小趣智品科技有限公司</span>&#x000A;<span id="LC499" class="line">- 499、广州石竹计算机软件有限公司</span>&#x000A;<span id="LC500" class="line">- 500、深圳市惟客数据科技有限公司</span>&#x000A;<span id="LC501" class="line">- 501、中国医疗器械有限公司</span>&#x000A;<span id="LC502" class="line">- 502、上海云谦科技有限公司</span>&#x000A;<span id="LC503" class="line">- 503、上海磐农信息科技有限公司</span>&#x000A;<span id="LC504" class="line">- 504、广州领航食品有限公司</span>&#x000A;<span id="LC505" class="line">- 505、青岛掌讯通区块链科技有限公司</span>&#x000A;<span id="LC506" class="line">- 506、北京新网数码信息技术有限公司</span>&#x000A;<span id="LC507" class="line">- 507、超体信息科技(深圳)有限公司</span>&#x000A;<span id="LC508" class="line">- 508、长沙店帮手信息科技有限公司</span>&#x000A;<span id="LC509" class="line">- 509、上海助弓装饰工程有限公司</span>&#x000A;<span id="LC510" class="line">- 510、杭州寻联网络科技有限公司</span>&#x000A;<span id="LC511" class="line">- 511、成都大淘客科技有限公司</span>&#x000A;<span id="LC512" class="line">- 512、松果出行</span>&#x000A;<span id="LC513" class="line">- 513、深圳市唤梦科技有限公司</span>&#x000A;<span id="LC514" class="line">- 514、上汽集团商用车技术中心</span>&#x000A;<span id="LC515" class="line">- 515、北京中航讯科技股份有限公司</span>&#x000A;<span id="LC516" class="line">- 516、北龙中网(北京)科技有限责任公司</span>&#x000A;<span id="LC517" class="line">- 517、前海超级前台(深圳)信息技术有限公司</span>&#x000A;<span id="LC518" class="line">- 518、上海中商网络股份有限公司</span>&#x000A;<span id="LC519" class="line">- 519、上海助通信息科技有限公司</span>&#x000A;<span id="LC520" class="line">- 520、宁波聚臻智能科技有限公司</span>&#x000A;<span id="LC521" class="line">- 521、上海零动数码科技股份有限公司</span>&#x000A;<span id="LC522" class="line">- 522、浙江学海教育科技有限公司</span>&#x000A;<span id="LC523" class="line">- 523、聚学云(山东)信息技术有限公司</span>&#x000A;<span id="LC524" class="line">- 524、多氟多新材料股份有限公司</span>&#x000A;<span id="LC525" class="line">- 525、智慧眼科技股份有限公司</span>&#x000A;<span id="LC526" class="line">- 526、广东智通人才连锁股份有限公司</span>&#x000A;<span id="LC527" class="line">- 527、世纪开元智印互联科技集团股份有限公司</span>&#x000A;<span id="LC528" class="line">- 528、北京理想汽车【理想汽车】</span>&#x000A;<span id="LC529" class="line">- 529、巽逸科技(重庆)有限公司</span>&#x000A;<span id="LC530" class="line">- 530、义乌购电子商务有限公司</span>&#x000A;<span id="LC531" class="line">- 531、深圳市珂莱蒂尔服饰有限公司</span>&#x000A;<span id="LC532" class="line">- 532、江西国泰利民信息科技有限公司</span>&#x000A;<span id="LC533" class="line">- 533、广西广电大数据科技有限公司</span>&#x000A;<span id="LC534" class="line">- 534、杭州艾麦科技有限公司</span>&#x000A;<span id="LC535" class="line">- 535、广州小滴科技有限公司</span>&#x000A;<span id="LC536" class="line">- 536、佳缘科技股份有限公司</span>&#x000A;<span id="LC537" class="line">- 537、上海深擎信息科技有限公司</span>&#x000A;<span id="LC538" class="line">- 538、武商网</span>&#x000A;<span id="LC539" class="line">- 539、福建民本信息科技有限公司</span>&#x000A;<span id="LC540" class="line">- 540、杭州惠合信息科技有限公司</span>&#x000A;<span id="LC541" class="line">- 541、厦门爱立得科技有限公司</span>&#x000A;<span id="LC542" class="line">- 542、成都拟合未来科技有限公司</span>&#x000A;<span id="LC543" class="line">- 543、宁波聚臻智能科技有限公司</span>&#x000A;<span id="LC544" class="line">- 544、广东百慧科技有限公司</span>&#x000A;<span id="LC545" class="line">- 545、笨马网络</span>&#x000A;<span id="LC546" class="line">- 546、深圳市信安数字科技有限公司</span>&#x000A;<span id="LC547" class="line">- 547、深圳市思乐数据技术有限公司</span>&#x000A;<span id="LC548" class="line">- 548、四川绿源集科技有限公司</span>&#x000A;<span id="LC549" class="line">- 549、湖南云医链生物科技有限公司</span>&#x000A;<span id="LC550" class="line">- 550、杭州源诚科技有限公司</span>&#x000A;<span id="LC551" class="line">- 551、北京开课吧科技有限公司</span>&#x000A;<span id="LC552" class="line">- 552、北京多来点信息技术有限公司</span>&#x000A;<span id="LC553" class="line">- 553、JEECG BOOT低代码开发平台</span>&#x000A;<span id="LC554" class="line">- 554、苏州同元软控信息技术有限公司</span>&#x000A;<span id="LC555" class="line">- 555、江苏大泰信息技术有限公司</span>&#x000A;<span id="LC556" class="line">- 556、北京大禹汇智</span>&#x000A;<span id="LC557" class="line">- 557、北京盛哲科技有限公司</span>&#x000A;<span id="LC558" class="line">- ……</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<blockquote>&#x000A;<p>更多接入的公司，欢迎在 <a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Fissues%2F1">登记地址</a> 登记，登记仅仅为了产品推广。</p>&#x000A;</blockquote>&#x000A;<p>欢迎大家的关注和使用，XXL-JOB也将拥抱变化，持续发展。</p>&#x000A;<h3>&#x000A;<a id="user-content-15-下载" class="anchor" href="#15-%E4%B8%8B%E8%BD%BD"></a>1.5 下载</h3>&#x000A;<h4>&#x000A;<a id="user-content-文档地址" class="anchor" href="#%E6%96%87%E6%A1%A3%E5%9C%B0%E5%9D%80"></a>文档地址</h4>&#x000A;<ul>&#x000A;<li><a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fxxl-job%2F">中文文档</a></li>&#x000A;<li><a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fxxl-job%2Fen%2F">English Documentation</a></li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-源码仓库地址" class="anchor" href="#%E6%BA%90%E7%A0%81%E4%BB%93%E5%BA%93%E5%9C%B0%E5%9D%80"></a>源码仓库地址</h4>&#x000A;<table>&#x000A;<thead>&#x000A;<tr>&#x000A;<th>源码仓库地址</th>&#x000A;<th>Release Download</th>&#x000A;</tr>&#x000A;</thead>&#x000A;<tbody>&#x000A;<tr>&#x000A;<td><a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job">https://github.com/xuxueli/xxl-job</a></td>&#x000A;<td><a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Freleases">Download</a></td>&#x000A;</tr>&#x000A;<tr>&#x000A;<td><a href="http://gitee.com/xuxueli0323/xxl-job" rel="nofollow">http://gitee.com/xuxueli0323/xxl-job</a></td>&#x000A;<td><a href="http://gitee.com/xuxueli0323/xxl-job/releases" rel="nofollow">Download</a></td>&#x000A;</tr>&#x000A;</tbody>&#x000A;</table>&#x000A;<h4>&#x000A;<a id="user-content-中央仓库地址" class="anchor" href="#%E4%B8%AD%E5%A4%AE%E4%BB%93%E5%BA%93%E5%9C%B0%E5%9D%80"></a>中央仓库地址</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">&lt;!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ --&gt;</span>&#x000A;<span id="LC2" class="line">&lt;dependency&gt;</span>&#x000A;<span id="LC3" class="line">    &lt;groupId&gt;com.xuxueli&lt;/groupId&gt;</span>&#x000A;<span id="LC4" class="line">    &lt;artifactId&gt;xxl-job-core&lt;/artifactId&gt;</span>&#x000A;<span id="LC5" class="line">    &lt;version&gt;${最新稳定版本}&lt;/version&gt;</span>&#x000A;<span id="LC6" class="line">&lt;/dependency&gt;</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-16-环境" class="anchor" href="#16-%E7%8E%AF%E5%A2%83"></a>1.6 环境</h3>&#x000A;<ul>&#x000A;<li>Maven3+</li>&#x000A;<li>Jdk1.8+</li>&#x000A;<li>Mysql5.7+</li>&#x000A;</ul>&#x000A;<h2>&#x000A;<a id="user-content-二快速入门" class="anchor" href="#%E4%BA%8C%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8"></a>二、快速入门</h2>&#x000A;<h3>&#x000A;<a id="user-content-21-初始化调度数据库" class="anchor" href="#21-%E5%88%9D%E5%A7%8B%E5%8C%96%E8%B0%83%E5%BA%A6%E6%95%B0%E6%8D%AE%E5%BA%93"></a>2.1 初始化“调度数据库”</h3>&#x000A;<p>请下载项目源码并解压，获取 "调度数据库初始化SQL脚本" 并执行即可。</p>&#x000A;<p>"调度数据库初始化SQL脚本" 位置为:</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">/xxl-job/doc/db/tables_xxl_job.sql</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>调度中心支持集群部署，集群情况下各节点务必连接同一个mysql实例;</p>&#x000A;<p>如果mysql做主从,调度中心集群节点务必强制走主库;</p>&#x000A;<h3>&#x000A;<a id="user-content-22-编译源码" class="anchor" href="#22-%E7%BC%96%E8%AF%91%E6%BA%90%E7%A0%81"></a>2.2 编译源码</h3>&#x000A;<p>解压源码,按照maven格式将源码导入IDE, 使用maven进行编译即可，源码结构如下：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">xxl-job-admin：调度中心</span>&#x000A;<span id="LC2" class="line">xxl-job-core：公共依赖</span>&#x000A;<span id="LC3" class="line">xxl-job-executor-samples：执行器Sample示例（选择合适的版本执行器，可直接使用，也可以参考其并将现有项目改造成执行器）</span>&#x000A;<span id="LC4" class="line">    ：xxl-job-executor-sample-springboot：Springboot版本，通过Springboot管理执行器，推荐这种方式；</span>&#x000A;<span id="LC5" class="line">    ：xxl-job-executor-sample-frameless：无框架版本；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-23-配置部署调度中心" class="anchor" href="#23-%E9%85%8D%E7%BD%AE%E9%83%A8%E7%BD%B2%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83"></a>2.3 配置部署“调度中心”</h3>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">调度中心项目：xxl-job-admin</span>&#x000A;<span id="LC2" class="line">作用：统一管理任务调度平台上调度任务，负责触发调度执行，并且提供任务管理平台。</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤一调度中心配置" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E9%85%8D%E7%BD%AE"></a>步骤一：调度中心配置：</h4>&#x000A;<p>调度中心配置文件地址：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">/xxl-job/xxl-job-admin/src/main/resources/application.properties</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>调度中心配置内容说明：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">### 调度中心JDBC链接：链接地址请保持和 2.1章节 所创建的调度数据库的地址一致</span>&#x000A;<span id="LC2" class="line">spring.datasource.url=jdbc:mysql://127.0.0.1:3306/xxl_job?useUnicode=true&amp;characterEncoding=UTF-8&amp;autoReconnect=true&amp;serverTimezone=Asia/Shanghai</span>&#x000A;<span id="LC3" class="line">spring.datasource.username=root</span>&#x000A;<span id="LC4" class="line">spring.datasource.password=root_pwd</span>&#x000A;<span id="LC5" class="line">spring.datasource.driver-class-name=com.mysql.jdbc.Driver</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">### 报警邮箱</span>&#x000A;<span id="LC8" class="line">spring.mail.host=smtp.qq.com</span>&#x000A;<span id="LC9" class="line">spring.mail.port=25</span>&#x000A;<span id="LC10" class="line">spring.mail.username=xxx@qq.com</span>&#x000A;<span id="LC11" class="line">spring.mail.password=xxx</span>&#x000A;<span id="LC12" class="line">spring.mail.properties.mail.smtp.auth=true</span>&#x000A;<span id="LC13" class="line">spring.mail.properties.mail.smtp.starttls.enable=true</span>&#x000A;<span id="LC14" class="line">spring.mail.properties.mail.smtp.starttls.required=true</span>&#x000A;<span id="LC15" class="line">spring.mail.properties.mail.smtp.socketFactory.class=javax.net.ssl.SSLSocketFactory</span>&#x000A;<span id="LC16" class="line"></span>&#x000A;<span id="LC17" class="line">### 调度中心通讯TOKEN [选填]：非空时启用；</span>&#x000A;<span id="LC18" class="line">xxl.job.accessToken=</span>&#x000A;<span id="LC19" class="line"></span>&#x000A;<span id="LC20" class="line">### 调度中心国际化配置 [必填]： 默认为 "zh_CN"/中文简体, 可选范围为 "zh_CN"/中文简体, "zh_TC"/中文繁体 and "en"/英文；</span>&#x000A;<span id="LC21" class="line">xxl.job.i18n=zh_CN</span>&#x000A;<span id="LC22" class="line"></span>&#x000A;<span id="LC23" class="line">## 调度线程池最大线程配置【必填】</span>&#x000A;<span id="LC24" class="line">xxl.job.triggerpool.fast.max=200</span>&#x000A;<span id="LC25" class="line">xxl.job.triggerpool.slow.max=100</span>&#x000A;<span id="LC26" class="line"></span>&#x000A;<span id="LC27" class="line">### 调度中心日志表数据保存天数 [必填]：过期日志自动清理；限制大于等于7时生效，否则, 如-1，关闭自动清理功能；</span>&#x000A;<span id="LC28" class="line">xxl.job.logretentiondays=30</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤二部署项目" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E9%83%A8%E7%BD%B2%E9%A1%B9%E7%9B%AE"></a>步骤二：部署项目：</h4>&#x000A;<p>如果已经正确进行上述配置，可将项目编译打包部署。</p>&#x000A;<p>调度中心访问地址：<a href="https://gitee.com/link?target=http%3A%2F%2Flocalhost%3A8080%2Fxxl-job-admin">http://localhost:8080/xxl-job-admin</a> (该地址执行器将会使用到，作为回调地址)</p>&#x000A;<p>默认登录账号 "admin/123456", 登录后运行界面如下图所示。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_6yC0.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p>至此“调度中心”项目已经部署成功。</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤三调度中心集群可选" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%89%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E9%9B%86%E7%BE%A4%E5%8F%AF%E9%80%89"></a>步骤三：调度中心集群（可选）：</h4>&#x000A;<p>调度中心支持集群部署，提升调度系统容灾和可用性。</p>&#x000A;<p>调度中心集群部署时，几点要求和建议：</p>&#x000A;<ul>&#x000A;<li>DB配置保持一致；</li>&#x000A;<li>集群机器时钟保持一致（单机集群忽视）；</li>&#x000A;<li>建议：推荐通过nginx为调度中心集群做负载均衡，分配域名。调度中心访问、执行器回调配置、调用API服务等操作均通过该域名进行。</li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-其他docker-镜像方式搭建调度中心" class="anchor" href="#%E5%85%B6%E4%BB%96docker-%E9%95%9C%E5%83%8F%E6%96%B9%E5%BC%8F%E6%90%AD%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83"></a>其他：Docker 镜像方式搭建调度中心：</h4>&#x000A;<ul>&#x000A;<li>下载镜像</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">// Docker地址：https://hub.docker.com/r/xuxueli/xxl-job-admin/     (建议指定版本号)</span>&#x000A;<span id="LC2" class="line">docker pull xuxueli/xxl-job-admin</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<ul>&#x000A;<li>创建容器并运行</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">docker run -p 8080:8080 -v /tmp:/data/applogs --name xxl-job-admin  -d xuxueli/xxl-job-admin:{指定版本}</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">/**</span>&#x000A;<span id="LC4" class="line">* 如需自定义 mysql 等配置，可通过 "-e PARAMS" 指定，参数格式 PARAMS="--key=value  --key2=value2" ；</span>&#x000A;<span id="LC5" class="line">* 配置项参考文件：/xxl-job/xxl-job-admin/src/main/resources/application.properties</span>&#x000A;<span id="LC6" class="line">* 如需自定义 JVM内存参数 等配置，可通过 "-e JAVA_OPTS" 指定，参数格式 JAVA_OPTS="-Xmx512m" ；</span>&#x000A;<span id="LC7" class="line">*/</span>&#x000A;<span id="LC8" class="line">docker run -e PARAMS="--spring.datasource.url=jdbc:mysql://127.0.0.1:3306/xxl_job?useUnicode=true&amp;characterEncoding=UTF-8&amp;autoReconnect=true&amp;serverTimezone=Asia/Shanghai" -p 8080:8080 -v /tmp:/data/applogs --name xxl-job-admin  -d xuxueli/xxl-job-admin:{指定版本}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-24-配置部署执行器项目" class="anchor" href="#24-%E9%85%8D%E7%BD%AE%E9%83%A8%E7%BD%B2%E6%89%A7%E8%A1%8C%E5%99%A8%E9%A1%B9%E7%9B%AE"></a>2.4 配置部署“执行器项目”</h3>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">“执行器”项目：xxl-job-executor-sample-springboot (提供多种版本执行器供选择，现以 springboot 版本为例，可直接使用，也可以参考其并将现有项目改造成执行器)</span>&#x000A;<span id="LC2" class="line">作用：负责接收“调度中心”的调度并执行；可直接部署执行器，也可以将执行器集成到现有业务项目中。</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤一maven依赖" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80maven%E4%BE%9D%E8%B5%96"></a>步骤一：maven依赖</h4>&#x000A;<p>确认pom文件中引入了 "xxl-job-core" 的maven依赖；</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二执行器配置" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E6%89%A7%E8%A1%8C%E5%99%A8%E9%85%8D%E7%BD%AE"></a>步骤二：执行器配置</h4>&#x000A;<p>执行器配置，配置文件地址：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">/xxl-job/xxl-job-executor-samples/xxl-job-executor-sample-springboot/src/main/resources/application.properties</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>执行器配置，配置内容说明：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">### 调度中心部署根地址 [选填]：如调度中心集群部署存在多个地址则用逗号分隔。执行器将会使用该地址进行"执行器心跳注册"和"任务结果回调"；为空则关闭自动注册；</span>&#x000A;<span id="LC2" class="line">xxl.job.admin.addresses=http://127.0.0.1:8080/xxl-job-admin</span>&#x000A;<span id="LC3" class="line"></span>&#x000A;<span id="LC4" class="line">### 执行器通讯TOKEN [选填]：非空时启用；</span>&#x000A;<span id="LC5" class="line">xxl.job.accessToken=</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">### 执行器AppName [选填]：执行器心跳注册分组依据；为空则关闭自动注册</span>&#x000A;<span id="LC8" class="line">xxl.job.executor.appname=xxl-job-executor-sample</span>&#x000A;<span id="LC9" class="line">### 执行器注册 [选填]：优先使用该配置作为注册地址，为空时使用内嵌服务 ”IP:PORT“ 作为注册地址。从而更灵活的支持容器类型执行器动态IP和动态映射端口问题。</span>&#x000A;<span id="LC10" class="line">xxl.job.executor.address=</span>&#x000A;<span id="LC11" class="line">### 执行器IP [选填]：默认为空表示自动获取IP，多网卡时可手动设置指定IP，该IP不会绑定Host仅作为通讯实用；地址信息用于 "执行器注册" 和 "调度中心请求并触发任务"；</span>&#x000A;<span id="LC12" class="line">xxl.job.executor.ip=</span>&#x000A;<span id="LC13" class="line">### 执行器端口号 [选填]：小于等于0则自动获取；默认端口为9999，单机部署多个执行器时，注意要配置不同执行器端口；</span>&#x000A;<span id="LC14" class="line">xxl.job.executor.port=9999</span>&#x000A;<span id="LC15" class="line">### 执行器运行日志文件存储磁盘路径 [选填] ：需要对该路径拥有读写权限；为空则使用默认路径；</span>&#x000A;<span id="LC16" class="line">xxl.job.executor.logpath=/data/applogs/xxl-job/jobhandler</span>&#x000A;<span id="LC17" class="line">### 执行器日志文件保存天数 [选填] ： 过期日志自动清理, 限制值大于等于3时生效; 否则, 如-1, 关闭自动清理功能；</span>&#x000A;<span id="LC18" class="line">xxl.job.executor.logretentiondays=30</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤三执行器组件配置" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%89%E6%89%A7%E8%A1%8C%E5%99%A8%E7%BB%84%E4%BB%B6%E9%85%8D%E7%BD%AE"></a>步骤三：执行器组件配置</h4>&#x000A;<p>执行器组件，配置文件地址：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">/xxl-job/xxl-job-executor-samples/xxl-job-executor-sample-springboot/src/main/java/com/xxl/job/executor/core/config/XxlJobConfig.java</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>执行器组件，配置内容说明：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">@Bean</span>&#x000A;<span id="LC2" class="line">public XxlJobSpringExecutor xxlJobExecutor() {</span>&#x000A;<span id="LC3" class="line">    logger.info("&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt; xxl-job config init.");</span>&#x000A;<span id="LC4" class="line">    XxlJobSpringExecutor xxlJobSpringExecutor = new XxlJobSpringExecutor();</span>&#x000A;<span id="LC5" class="line">    xxlJobSpringExecutor.setAdminAddresses(adminAddresses);</span>&#x000A;<span id="LC6" class="line">    xxlJobSpringExecutor.setAppname(appname);</span>&#x000A;<span id="LC7" class="line">    xxlJobSpringExecutor.setIp(ip);</span>&#x000A;<span id="LC8" class="line">    xxlJobSpringExecutor.setPort(port);</span>&#x000A;<span id="LC9" class="line">    xxlJobSpringExecutor.setAccessToken(accessToken);</span>&#x000A;<span id="LC10" class="line">    xxlJobSpringExecutor.setLogPath(logPath);</span>&#x000A;<span id="LC11" class="line">    xxlJobSpringExecutor.setLogRetentionDays(logRetentionDays);</span>&#x000A;<span id="LC12" class="line"></span>&#x000A;<span id="LC13" class="line">    return xxlJobSpringExecutor;</span>&#x000A;<span id="LC14" class="line">}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤四部署执行器项目" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E5%9B%9B%E9%83%A8%E7%BD%B2%E6%89%A7%E8%A1%8C%E5%99%A8%E9%A1%B9%E7%9B%AE"></a>步骤四：部署执行器项目：</h4>&#x000A;<p>如果已经正确进行上述配置，可将执行器项目编译打部署，系统提供多种执行器Sample示例项目，选择其中一个即可，各自的部署方式如下。</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">xxl-job-executor-sample-springboot：项目编译打包成springboot类型的可执行JAR包，命令启动即可；</span>&#x000A;<span id="LC2" class="line">xxl-job-executor-sample-frameless：项目编译打包成JAR包，命令启动即可；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>至此“执行器”项目已经部署结束。</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤五执行器集群可选" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%94%E6%89%A7%E8%A1%8C%E5%99%A8%E9%9B%86%E7%BE%A4%E5%8F%AF%E9%80%89"></a>步骤五：执行器集群（可选）：</h4>&#x000A;<p>执行器支持集群部署，提升调度系统可用性，同时提升任务处理能力。</p>&#x000A;<p>执行器集群部署时，几点要求和建议：</p>&#x000A;<ul>&#x000A;<li>执行器回调地址（xxl.job.admin.addresses）需要保持一致；执行器根据该配置进行执行器自动注册等操作。</li>&#x000A;<li>同一个执行器集群内AppName（xxl.job.executor.appname）需要保持一致；调度中心根据该配置动态发现不同集群的在线执行器列表。</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-25-开发第一个任务hello-world" class="anchor" href="#25-%E5%BC%80%E5%8F%91%E7%AC%AC%E4%B8%80%E4%B8%AA%E4%BB%BB%E5%8A%A1hello-world"></a>2.5 开发第一个任务“Hello World”</h3>&#x000A;<p>本示例以新建一个 “GLUE模式(Java)” 运行模式的任务为例。更多有关任务的详细配置，请查看“章节三：任务详解”。&#x000A;（ “GLUE模式(Java)”的执行代码托管到调度中心在线维护，相比“Bean模式任务”需要在执行器项目开发部署上线，更加简便轻量）</p>&#x000A;<blockquote>&#x000A;<p>前提：请确认“调度中心”和“执行器”项目已经成功部署并启动；</p>&#x000A;</blockquote>&#x000A;<h4>&#x000A;<a id="user-content-步骤一新建任务" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E6%96%B0%E5%BB%BA%E4%BB%BB%E5%8A%A1"></a>步骤一：新建任务：</h4>&#x000A;<p>登录调度中心，点击下图所示“新建任务”按钮，新建示例任务。然后，参考下面截图中任务的参数配置，点击保存。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_o8HQ.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAsz.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二glue模式java-任务开发" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8Cglue%E6%A8%A1%E5%BC%8Fjava-%E4%BB%BB%E5%8A%A1%E5%BC%80%E5%8F%91"></a>步骤二：“GLUE模式(Java)” 任务开发：</h4>&#x000A;<p>请点击任务右侧 “GLUE” 按钮，进入 “GLUE编辑器开发界面” ，见下图。“GLUE模式(Java)” 运行模式的任务默认已经初始化了示例任务代码，即打印Hello World。&#x000A;（ “GLUE模式(Java)” 运行模式的任务实际上是一段继承自IJobHandler的Java类代码，它在执行器项目中运行，可使用@Resource/@Autowire注入执行器里中的其他服务，详细介绍请查看第三章节）</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Fgql.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_dNUJ.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h4>&#x000A;<a id="user-content-步骤三触发执行" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%89%E8%A7%A6%E5%8F%91%E6%89%A7%E8%A1%8C"></a>步骤三：触发执行：</h4>&#x000A;<p>请点击任务右侧 “执行” 按钮，可手动触发一次任务执行（通常情况下，通过配置Cron表达式进行任务调度触发）。</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤四查看日志" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E5%9B%9B%E6%9F%A5%E7%9C%8B%E6%97%A5%E5%BF%97"></a>步骤四：查看日志：</h4>&#x000A;<p>请点击任务右侧 “日志” 按钮，可前往任务日志界面查看任务日志。&#x000A;在任务日志界面中，可查看该任务的历史调度记录以及每一次调度的任务调度信息、执行参数和执行信息。运行中的任务点击右侧的“执行日志”按钮，可进入日志控制台查看实时执行日志。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_inc8.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p>在日志控制台，可以Rolling方式实时查看任务在执行器一侧运行输出的日志信息，实时监控任务进度；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_eYrv.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h2>&#x000A;<a id="user-content-三任务详解" class="anchor" href="#%E4%B8%89%E4%BB%BB%E5%8A%A1%E8%AF%A6%E8%A7%A3"></a>三、任务详解</h2>&#x000A;<h3>&#x000A;<a id="user-content-配置属性详细说明" class="anchor" href="#%E9%85%8D%E7%BD%AE%E5%B1%9E%E6%80%A7%E8%AF%A6%E7%BB%86%E8%AF%B4%E6%98%8E"></a>配置属性详细说明：</h3>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">基础配置：</span>&#x000A;<span id="LC2" class="line">    - 执行器：任务的绑定的执行器，任务触发调度时将会自动发现注册成功的执行器, 实现任务自动发现功能; 另一方面也可以方便的进行任务分组。每个任务必须绑定一个执行器, 可在 "执行器管理" 进行设置;</span>&#x000A;<span id="LC3" class="line">    - 任务描述：任务的描述信息，便于任务管理；</span>&#x000A;<span id="LC4" class="line">    - 负责人：任务的负责人；</span>&#x000A;<span id="LC5" class="line">    - 报警邮件：任务调度失败时邮件通知的邮箱地址，支持配置多邮箱地址，配置多个邮箱地址时用逗号分隔；</span>&#x000A;<span id="LC6" class="line">    </span>&#x000A;<span id="LC7" class="line">触发配置：</span>&#x000A;<span id="LC8" class="line">    - 调度类型：</span>&#x000A;<span id="LC9" class="line">        无：该类型不会主动触发调度；</span>&#x000A;<span id="LC10" class="line">        CRON：该类型将会通过CRON，触发任务调度；</span>&#x000A;<span id="LC11" class="line">        固定速度：该类型将会以固定速度，触发任务调度；按照固定的间隔时间，周期性触发；</span>&#x000A;<span id="LC12" class="line">        固定延迟：该类型将会以固定延迟，触发任务调度；按照固定的延迟时间，从上次调度结束后开始计算延迟时间，到达延迟时间后触发下次调度；</span>&#x000A;<span id="LC13" class="line">    - CRON：触发任务执行的Cron表达式；</span>&#x000A;<span id="LC14" class="line">    - 固定速度：固件速度的时间间隔，单位为秒；</span>&#x000A;<span id="LC15" class="line">    - 固定延迟：固件延迟的时间间隔，单位为秒；</span>&#x000A;<span id="LC16" class="line">    </span>&#x000A;<span id="LC17" class="line">任务配置：</span>&#x000A;<span id="LC18" class="line">    - 运行模式：</span>&#x000A;<span id="LC19" class="line">        BEAN模式：任务以JobHandler方式维护在执行器端；需要结合 "JobHandler" 属性匹配执行器中任务；</span>&#x000A;<span id="LC20" class="line">        GLUE模式(Java)：任务以源码方式维护在调度中心；该模式的任务实际上是一段继承自IJobHandler的Java类代码并 "groovy" 源码方式维护，它在执行器项目中运行，可使用@Resource/@Autowire注入执行器里中的其他服务；</span>&#x000A;<span id="LC21" class="line">        GLUE模式(Shell)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 "shell" 脚本；</span>&#x000A;<span id="LC22" class="line">        GLUE模式(Python)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 "python" 脚本；</span>&#x000A;<span id="LC23" class="line">        GLUE模式(PHP)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 "php" 脚本；</span>&#x000A;<span id="LC24" class="line">        GLUE模式(NodeJS)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 "nodejs" 脚本；</span>&#x000A;<span id="LC25" class="line">        GLUE模式(PowerShell)：任务以源码方式维护在调度中心；该模式的任务实际上是一段 "PowerShell" 脚本；</span>&#x000A;<span id="LC26" class="line">    - JobHandler：运行模式为 "BEAN模式" 时生效，对应执行器中新开发的JobHandler类“@JobHandler”注解自定义的value值；</span>&#x000A;<span id="LC27" class="line">    - 执行参数：任务执行所需的参数；     </span>&#x000A;<span id="LC28" class="line">    </span>&#x000A;<span id="LC29" class="line">高级配置：</span>&#x000A;<span id="LC30" class="line">    - 路由策略：当执行器集群部署时，提供丰富的路由策略，包括；</span>&#x000A;<span id="LC31" class="line">        FIRST（第一个）：固定选择第一个机器；</span>&#x000A;<span id="LC32" class="line">        LAST（最后一个）：固定选择最后一个机器；</span>&#x000A;<span id="LC33" class="line">        ROUND（轮询）：；</span>&#x000A;<span id="LC34" class="line">        RANDOM（随机）：随机选择在线的机器；</span>&#x000A;<span id="LC35" class="line">        CONSISTENT_HASH（一致性HASH）：每个任务按照Hash算法固定选择某一台机器，且所有任务均匀散列在不同机器上。</span>&#x000A;<span id="LC36" class="line">        LEAST_FREQUENTLY_USED（最不经常使用）：使用频率最低的机器优先被选举；</span>&#x000A;<span id="LC37" class="line">        LEAST_RECENTLY_USED（最近最久未使用）：最久未使用的机器优先被选举；</span>&#x000A;<span id="LC38" class="line">        FAILOVER（故障转移）：按照顺序依次进行心跳检测，第一个心跳检测成功的机器选定为目标执行器并发起调度；</span>&#x000A;<span id="LC39" class="line">        BUSYOVER（忙碌转移）：按照顺序依次进行空闲检测，第一个空闲检测成功的机器选定为目标执行器并发起调度；</span>&#x000A;<span id="LC40" class="line">        SHARDING_BROADCAST(分片广播)：广播触发对应集群中所有机器执行一次任务，同时系统自动传递分片参数；可根据分片参数开发分片任务；</span>&#x000A;<span id="LC41" class="line">    - 子任务：每个任务都拥有一个唯一的任务ID(任务ID可以从任务列表获取)，当本任务执行结束并且执行成功时，将会触发子任务ID所对应的任务的一次主动调度。</span>&#x000A;<span id="LC42" class="line">    - 调度过期策略：</span>&#x000A;<span id="LC43" class="line">        - 忽略：调度过期后，忽略过期的任务，从当前时间开始重新计算下次触发时间；</span>&#x000A;<span id="LC44" class="line">        - 立即执行一次：调度过期后，立即执行一次，并从当前时间开始重新计算下次触发时间；</span>&#x000A;<span id="LC45" class="line">    - 阻塞处理策略：调度过于密集执行器来不及处理时的处理策略；</span>&#x000A;<span id="LC46" class="line">        单机串行（默认）：调度请求进入单机执行器后，调度请求进入FIFO队列并以串行方式运行；</span>&#x000A;<span id="LC47" class="line">        丢弃后续调度：调度请求进入单机执行器后，发现执行器存在运行的调度任务，本次请求将会被丢弃并标记为失败；</span>&#x000A;<span id="LC48" class="line">        覆盖之前调度：调度请求进入单机执行器后，发现执行器存在运行的调度任务，将会终止运行中的调度任务并清空队列，然后运行本地调度任务；</span>&#x000A;<span id="LC49" class="line">    - 任务超时时间：支持自定义任务超时时间，任务运行超时将会主动中断任务；</span>&#x000A;<span id="LC50" class="line">    - 失败重试次数；支持自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-31-bean模式类形式" class="anchor" href="#31-bean%E6%A8%A1%E5%BC%8F%E7%B1%BB%E5%BD%A2%E5%BC%8F"></a>3.1 BEAN模式（类形式）</h3>&#x000A;<p>Bean模式任务，支持基于类的开发方式，每个任务对应一个Java类。</p>&#x000A;<ul>&#x000A;<li>优点：不限制项目环境，兼容性好。即使是无框架项目，如main方法直接启动的项目也可以提供支持，可以参考示例项目 "xxl-job-executor-sample-frameless"；</li>&#x000A;<li>缺点：&#x000A;<ul>&#x000A;<li>每个任务需要占用一个Java类，造成类的浪费；</li>&#x000A;<li>不支持自动扫描任务并注入到执行器容器，需要手动注入。</li>&#x000A;</ul>&#x000A;</li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-步骤一执行器项目中开发job类" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E6%89%A7%E8%A1%8C%E5%99%A8%E9%A1%B9%E7%9B%AE%E4%B8%AD%E5%BC%80%E5%8F%91job%E7%B1%BB"></a>步骤一：执行器项目中，开发Job类：</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">1、开发一个继承自"com.xxl.job.core.handler.IJobHandler"的JobHandler类，实现其中任务方法。</span>&#x000A;<span id="LC2" class="line">2、手动通过如下方式注入到执行器容器。</span>&#x000A;<span id="LC3" class="line">```</span>&#x000A;<span id="LC4" class="line">XxlJobExecutor.registJobHandler("demoJobHandler", new DemoJobHandler());</span>&#x000A;<span id="LC5" class="line">```</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤二调度中心新建调度任务" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1"></a>步骤二：调度中心，新建调度任务</h4>&#x000A;<p>后续步骤和 "3.2 BEAN模式（方法形式）"一致，可以前往参考。</p>&#x000A;<h3>&#x000A;<a id="user-content-32-bean模式方法形式" class="anchor" href="#32-bean%E6%A8%A1%E5%BC%8F%E6%96%B9%E6%B3%95%E5%BD%A2%E5%BC%8F"></a>3.2 BEAN模式（方法形式）</h3>&#x000A;<p>Bean模式任务，支持基于方法的开发方式，每个任务对应一个方法。</p>&#x000A;<ul>&#x000A;<li>优点：&#x000A;<ul>&#x000A;<li>每个任务只需要开发一个方法，并添加"@XxlJob"注解即可，更加方便、快速。</li>&#x000A;<li>支持自动扫描任务并注入到执行器容器。</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>缺点：要求Spring容器环境；</li>&#x000A;</ul>&#x000A;<blockquote>&#x000A;<p>基于方法开发的任务，底层会生成JobHandler代理，和基于类的方式一样，任务也会以JobHandler的形式存在于执行器任务容器中。</p>&#x000A;</blockquote>&#x000A;<h4>&#x000A;<a id="user-content-步骤一执行器项目中开发job方法" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E6%89%A7%E8%A1%8C%E5%99%A8%E9%A1%B9%E7%9B%AE%E4%B8%AD%E5%BC%80%E5%8F%91job%E6%96%B9%E6%B3%95"></a>步骤一：执行器项目中，开发Job方法：</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">1、任务开发：在Spring Bean实例中，开发Job方法；</span>&#x000A;<span id="LC2" class="line">2、注解配置：为Job方法添加注解 "@XxlJob(value="自定义jobhandler名称", init = "JobHandler初始化方法", destroy = "JobHandler销毁方法")"，注解value值对应的是调度中心新建任务的JobHandler属性的值。</span>&#x000A;<span id="LC3" class="line">3、执行日志：需要通过 "XxlJobHelper.log" 打印执行日志；</span>&#x000A;<span id="LC4" class="line">4、任务结果：默认任务结果为 "成功" 状态，不需要主动设置；如有诉求，比如设置任务结果为失败，可以通过 "XxlJobHelper.handleFail/handleSuccess" 自主设置任务结果；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">// 可参考Sample示例执行器中的 "com.xxl.job.executor.service.jobhandler.SampleXxlJob" ，如下：</span>&#x000A;<span id="LC2" class="line">@XxlJob("demoJobHandler")</span>&#x000A;<span id="LC3" class="line">public void demoJobHandler() throws Exception {</span>&#x000A;<span id="LC4" class="line">    XxlJobHelper.log("XXL-JOB, Hello World.");</span>&#x000A;<span id="LC5" class="line">}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-步骤二调度中心新建调度任务-1" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1-1"></a>步骤二：调度中心，新建调度任务</h4>&#x000A;<p>参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 "BEAN模式"，JobHandler属性填写任务注解“@XxlJob”中定义的值；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAsz.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h4>&#x000A;<a id="user-content-原生内置bean模式任务" class="anchor" href="#%E5%8E%9F%E7%94%9F%E5%86%85%E7%BD%AEbean%E6%A8%A1%E5%BC%8F%E4%BB%BB%E5%8A%A1"></a>原生内置Bean模式任务</h4>&#x000A;<p>为方便用户参考与快速实用，示例执行器内原生提供多个Bean模式任务Handler，可以直接配置实用，如下：</p>&#x000A;<ul>&#x000A;<li>demoJobHandler：简单示例任务，任务内部模拟耗时任务逻辑，用户可在线体验Rolling Log等功能；</li>&#x000A;<li>shardingJobHandler：分片示例任务，任务内部模拟处理分片参数，可参考熟悉分片任务；</li>&#x000A;<li>httpJobHandler：通用HTTP任务Handler；业务方只需要提供HTTP链接等信息即可，不限制语言、平台。示例任务入参如下：&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">url: http://www.xxx.com</span>&#x000A;<span id="LC2" class="line">method: get 或 post</span>&#x000A;<span id="LC3" class="line">data: post-data</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;</li>&#x000A;<li>commandJobHandler：通用命令行任务Handler；业务方只需要提供命令行即可；如 “pwd”命令；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-33-glue模式java" class="anchor" href="#33-glue%E6%A8%A1%E5%BC%8Fjava"></a>3.3 GLUE模式(Java)</h3>&#x000A;<p>任务以源码方式维护在调度中心，支持通过Web IDE在线更新，实时编译和生效，因此不需要指定JobHandler。开发流程如下：</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤一调度中心新建调度任务" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1"></a>步骤一：调度中心，新建调度任务：</h4>&#x000A;<p>参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 "GLUE模式(Java)"；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_tJOq.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二开发任务代码" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E5%BC%80%E5%8F%91%E4%BB%BB%E5%8A%A1%E4%BB%A3%E7%A0%81"></a>步骤二：开发任务代码：</h4>&#x000A;<p>选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。</p>&#x000A;<p>版本回溯功能（支持30个版本的版本回溯）：在GLUE任务的Web IDE界面，选择右上角下拉框“版本回溯”，会列出该GLUE的更新历史，选择相应版本即可显示该版本代码，保存后GLUE代码即回退到对应的历史版本；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_dNUJ.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-34-glue模式shell" class="anchor" href="#34-glue%E6%A8%A1%E5%BC%8Fshell"></a>3.4 GLUE模式(Shell)</h3>&#x000A;<h4>&#x000A;<a id="user-content-步骤一调度中心新建调度任务-1" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1-1"></a>步骤一：调度中心，新建调度任务</h4>&#x000A;<p>参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 "GLUE模式(Shell)"；</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二开发任务代码-1" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E5%BC%80%E5%8F%91%E4%BB%BB%E5%8A%A1%E4%BB%A3%E7%A0%81-1"></a>步骤二：开发任务代码：</h4>&#x000A;<p>选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。</p>&#x000A;<p>该模式的任务实际上是一段 "shell" 脚本；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_iUw0.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-34-glue模式python" class="anchor" href="#34-glue%E6%A8%A1%E5%BC%8Fpython"></a>3.4 GLUE模式(Python)</h3>&#x000A;<h4>&#x000A;<a id="user-content-步骤一调度中心新建调度任务-2" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1-2"></a>步骤一：调度中心，新建调度任务</h4>&#x000A;<p>参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 "GLUE模式(Python)"；</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二开发任务代码-2" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E5%BC%80%E5%8F%91%E4%BB%BB%E5%8A%A1%E4%BB%A3%E7%A0%81-2"></a>步骤二：开发任务代码：</h4>&#x000A;<p>选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。</p>&#x000A;<p>该模式的任务实际上是一段 "python" 脚本；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_BPLG.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-35-glue模式nodejs" class="anchor" href="#35-glue%E6%A8%A1%E5%BC%8Fnodejs"></a>3.5 GLUE模式(NodeJS)</h3>&#x000A;<h4>&#x000A;<a id="user-content-步骤一调度中心新建调度任务-3" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%B8%80%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%96%B0%E5%BB%BA%E8%B0%83%E5%BA%A6%E4%BB%BB%E5%8A%A1-3"></a>步骤一：调度中心，新建调度任务</h4>&#x000A;<p>参考上文“配置属性详细说明”对新建的任务进行参数配置，运行模式选中 "GLUE模式(NodeJS)"；</p>&#x000A;<h4>&#x000A;<a id="user-content-步骤二开发任务代码-3" class="anchor" href="#%E6%AD%A5%E9%AA%A4%E4%BA%8C%E5%BC%80%E5%8F%91%E4%BB%BB%E5%8A%A1%E4%BB%A3%E7%A0%81-3"></a>步骤二：开发任务代码：</h4>&#x000A;<p>选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（也可以在IDE中开发完成后，复制粘贴到编辑中）。</p>&#x000A;<p>该模式的任务实际上是一段 "nodeJS" 脚本；</p>&#x000A;<h3>&#x000A;<a id="user-content-36-glue模式php" class="anchor" href="#36-glue%E6%A8%A1%E5%BC%8Fphp"></a>3.6 GLUE模式(PHP)</h3>&#x000A;<p>同上</p>&#x000A;<h3>&#x000A;<a id="user-content-37-glue模式powershell" class="anchor" href="#37-glue%E6%A8%A1%E5%BC%8Fpowershell"></a>3.7 GLUE模式(PowerShell)</h3>&#x000A;<p>同上</p>&#x000A;<h2>&#x000A;<a id="user-content-四操作指南" class="anchor" href="#%E5%9B%9B%E6%93%8D%E4%BD%9C%E6%8C%87%E5%8D%97"></a>四、操作指南</h2>&#x000A;<h3>&#x000A;<a id="user-content-41-配置执行器" class="anchor" href="#41-%E9%85%8D%E7%BD%AE%E6%89%A7%E8%A1%8C%E5%99%A8"></a>4.1 配置执行器</h3>&#x000A;<p>点击进入"执行器管理"界面, 如下图:&#x000A;<img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Hr2T.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">1、"调度中心OnLine:"右侧显示在线的"调度中心"列表, 任务执行结束后, 将会以failover的模式进行回调调度中心通知执行结果, 避免回调的单点风险;</span>&#x000A;<span id="LC2" class="line">2、"执行器列表" 中显示在线的执行器列表, 可通过"OnLine 机器"查看对应执行器的集群机器。</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>点击按钮 "+新增执行器" 弹框如下图, 可新增执行器配置:</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_V3vF.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p>执行器属性说明</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">AppName: 是每个执行器集群的唯一标示AppName, 执行器会周期性以AppName为对象进行自动注册。可通过该配置自动发现注册成功的执行器, 供任务调度时使用;</span>&#x000A;<span id="LC2" class="line">名称: 执行器的名称, 因为AppName限制字母数字等组成,可读性不强, 名称为了提高执行器的可读性;</span>&#x000A;<span id="LC3" class="line">排序: 执行器的排序, 系统中需要执行器的地方,如任务新增, 将会按照该排序读取可用的执行器列表;</span>&#x000A;<span id="LC4" class="line">注册方式：调度中心获取执行器地址的方式；</span>&#x000A;<span id="LC5" class="line">    自动注册：执行器自动进行执行器注册，调度中心通过底层注册表可以动态发现执行器机器地址；</span>&#x000A;<span id="LC6" class="line">    手动录入：人工手动录入执行器的地址信息，多地址逗号分隔，供调度中心使用；</span>&#x000A;<span id="LC7" class="line">机器地址："注册方式"为"手动录入"时有效，支持人工维护执行器的地址信息；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-42-新建任务" class="anchor" href="#42-%E6%96%B0%E5%BB%BA%E4%BB%BB%E5%8A%A1"></a>4.2 新建任务</h3>&#x000A;<p>进入任务管理界面，点击“新增任务”按钮，在弹出的“新增任务”界面配置任务属性后保存即可。详情页参考章节 "三、任务详解"。</p>&#x000A;<h3>&#x000A;<a id="user-content-43-编辑任务" class="anchor" href="#43-%E7%BC%96%E8%BE%91%E4%BB%BB%E5%8A%A1"></a>4.3 编辑任务</h3>&#x000A;<p>进入任务管理界面，选中指定任务。点击该任务右侧“编辑”按钮，在弹出的“编辑任务”界面更新任务属性后保存即可，可以修改设置的任务属性信息：</p>&#x000A;<h3>&#x000A;<a id="user-content-44-编辑glue代码" class="anchor" href="#44-%E7%BC%96%E8%BE%91glue%E4%BB%A3%E7%A0%81"></a>4.4 编辑GLUE代码</h3>&#x000A;<p>该操作仅针对GLUE任务。</p>&#x000A;<p>选中指定任务，点击该任务右侧“GLUE”按钮，将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发。可参考章节 "3.3 GLUE模式(Java)"。</p>&#x000A;<h3>&#x000A;<a id="user-content-45-启动停止任务" class="anchor" href="#45-%E5%90%AF%E5%8A%A8%E5%81%9C%E6%AD%A2%E4%BB%BB%E5%8A%A1"></a>4.5 启动/停止任务</h3>&#x000A;<p>可对任务进行“启动”和“停止”操作。&#x000A;需要注意的是，此处的启动/停止仅针对任务的后续调度触发行为，不会影响到已经触发的调度任务，如需终止已经触发的调度任务，可查看“4.9 终止运行中的任务”</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-46-手动触发一次调度" class="anchor" href="#46-%E6%89%8B%E5%8A%A8%E8%A7%A6%E5%8F%91%E4%B8%80%E6%AC%A1%E8%B0%83%E5%BA%A6"></a>4.6 手动触发一次调度</h3>&#x000A;<p>点击“执行”按钮，可手动触发一次任务调度，不影响原有调度规则。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-47-查看调度日志" class="anchor" href="#47-%E6%9F%A5%E7%9C%8B%E8%B0%83%E5%BA%A6%E6%97%A5%E5%BF%97"></a>4.7 查看调度日志</h3>&#x000A;<p>点击“日志”按钮，可以查看任务历史调度日志。在历史调入日志界面可查看每次任务调度的调度结果、执行结果等，点击“执行日志”按钮可查看执行器完整日志。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_ZAhX.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_UDSo.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">调度时间："调度中心"触发本次调度并向"执行器"发送任务执行信号的时间；</span>&#x000A;<span id="LC2" class="line">调度结果："调度中心"触发本次调度的结果，200表示成功，500或其他表示失败；</span>&#x000A;<span id="LC3" class="line">调度备注："调度中心"触发本次调度的日志信息；</span>&#x000A;<span id="LC4" class="line">执行器地址：本次任务执行的机器地址</span>&#x000A;<span id="LC5" class="line">运行模式：触发调度时任务的运行模式，运行模式可参考章节 "三、任务详解"；</span>&#x000A;<span id="LC6" class="line">任务参数：本地任务执行的入参</span>&#x000A;<span id="LC7" class="line">执行时间："执行器"中本次任务执行结束后回调的时间；</span>&#x000A;<span id="LC8" class="line">执行结果："执行器"中本次任务执行的结果，200表示成功，500或其他表示失败；</span>&#x000A;<span id="LC9" class="line">执行备注："执行器"中本次任务执行的日志信息；</span>&#x000A;<span id="LC10" class="line">操作：</span>&#x000A;<span id="LC11" class="line">    "执行日志"按钮：点击可查看本地任务执行的详细日志信息；详见“4.8 查看执行日志”；</span>&#x000A;<span id="LC12" class="line">    "终止任务"按钮：点击可终止本地调度对应执行器上本任务的执行线程，包括未执行的阻塞任务一并被终止；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-48-查看执行日志" class="anchor" href="#48-%E6%9F%A5%E7%9C%8B%E6%89%A7%E8%A1%8C%E6%97%A5%E5%BF%97"></a>4.8 查看执行日志</h3>&#x000A;<p>点击执行日志右侧的 “执行日志” 按钮，可跳转至执行日志界面，可以查看业务代码中打印的完整日志，如下图；</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_tvGI.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-49-终止运行中的任务" class="anchor" href="#49-%E7%BB%88%E6%AD%A2%E8%BF%90%E8%A1%8C%E4%B8%AD%E7%9A%84%E4%BB%BB%E5%8A%A1"></a>4.9 终止运行中的任务</h3>&#x000A;<p>仅针对执行中的任务。&#x000A;在任务日志界面，点击右侧的“终止任务”按钮，将会向本次任务对应的执行器发送任务终止请求，将会终止掉本次任务，同时会清空掉整个任务执行队列。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_hIci.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p>任务终止时通过 "interrupt" 执行线程的方式实现, 将会触发 "InterruptedException" 异常。因此如果JobHandler内部catch到了该异常并消化掉的话, 任务终止功能将不可用。</p>&#x000A;<p>因此, 如果遇到上述任务终止不可用的情况, 需要在JobHandler中应该针对 "InterruptedException" 异常进行特殊处理 (向上抛出) , 正确逻辑如下:</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">try{</span>&#x000A;<span id="LC2" class="line">    // do something</span>&#x000A;<span id="LC3" class="line">} catch (Exception e) {</span>&#x000A;<span id="LC4" class="line">    if (e instanceof InterruptedException) {</span>&#x000A;<span id="LC5" class="line">        throw e;</span>&#x000A;<span id="LC6" class="line">    }</span>&#x000A;<span id="LC7" class="line">    logger.warn("{}", e);</span>&#x000A;<span id="LC8" class="line">}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>而且，在JobHandler中开启子线程时，子线程也不可catch处理"InterruptedException"，应该主动向上抛出。</p>&#x000A;<p>任务终止时会执行对应JobHandler的"destroy()"方法，可以借助该方法处理一些资源回收的逻辑。</p>&#x000A;<h3>&#x000A;<a id="user-content-410-删除执行日志" class="anchor" href="#410-%E5%88%A0%E9%99%A4%E6%89%A7%E8%A1%8C%E6%97%A5%E5%BF%97"></a>4.10 删除执行日志</h3>&#x000A;<p>在任务日志界面，选中执行器和任务之后，点击右侧的"删除"按钮将会出现"日志清理"弹框，弹框中支持选择不同类型的日志清理策略，选中后点击"确定"按钮即可进行日志清理操作；&#x000A;<img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Ypik.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_EB65.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-411-删除任务" class="anchor" href="#411-%E5%88%A0%E9%99%A4%E4%BB%BB%E5%8A%A1"></a>4.11 删除任务</h3>&#x000A;<p>点击删除按钮，可以删除对应任务。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Z9Qr.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-412-用户管理" class="anchor" href="#412-%E7%94%A8%E6%88%B7%E7%AE%A1%E7%90%86"></a>4.12 用户管理</h3>&#x000A;<p>进入 "用户管理" 界面，可查看和管理用户信息；</p>&#x000A;<p>目前用户分为两种角色：</p>&#x000A;<ul>&#x000A;<li>管理员：拥有全量权限，支持在线管理用户信息，为用户分配权限，权限分配粒度为执行器；</li>&#x000A;<li>普通用户：仅拥有被分配权限的执行器，及相关任务的操作权限；</li>&#x000A;</ul>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_1001.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_1002.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h2>&#x000A;<a id="user-content-五总体设计" class="anchor" href="#%E4%BA%94%E6%80%BB%E4%BD%93%E8%AE%BE%E8%AE%A1"></a>五、总体设计</h2>&#x000A;<h3>&#x000A;<a id="user-content-51-源码目录介绍" class="anchor" href="#51-%E6%BA%90%E7%A0%81%E7%9B%AE%E5%BD%95%E4%BB%8B%E7%BB%8D"></a>5.1 源码目录介绍</h3>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">- /doc :文档资料</span>&#x000A;<span id="LC2" class="line">- /db :“调度数据库”建表脚本</span>&#x000A;<span id="LC3" class="line">- /xxl-job-admin :调度中心，项目源码</span>&#x000A;<span id="LC4" class="line">- /xxl-job-core :公共Jar依赖</span>&#x000A;<span id="LC5" class="line">- /xxl-job-executor-samples :执行器，Sample示例项目（大家可以在该项目上进行开发，也可以将现有项目改造生成执行器项目）</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-52-调度数据库配置" class="anchor" href="#52-%E8%B0%83%E5%BA%A6%E6%95%B0%E6%8D%AE%E5%BA%93%E9%85%8D%E7%BD%AE"></a>5.2 “调度数据库”配置</h3>&#x000A;<p>XXL-JOB调度模块基于自研调度组件并支持集群部署，调度数据库表说明如下：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">- xxl_job_lock：任务调度锁表；</span>&#x000A;<span id="LC2" class="line">- xxl_job_group：执行器信息表，维护任务执行器信息；</span>&#x000A;<span id="LC3" class="line">- xxl_job_info：调度扩展信息表： 用于保存XXL-JOB调度任务的扩展信息，如任务分组、任务名、机器地址、执行器、执行入参和报警邮件等等；</span>&#x000A;<span id="LC4" class="line">- xxl_job_log：调度日志表： 用于保存XXL-JOB任务调度的历史信息，如调度结果、执行结果、调度入参、调度机器和执行器等等；</span>&#x000A;<span id="LC5" class="line">- xxl_job_log_report：调度日志报表：用户存储XXL-JOB任务调度日志的报表，调度中心报表功能页面会用到；</span>&#x000A;<span id="LC6" class="line">- xxl_job_logglue：任务GLUE日志：用于保存GLUE更新历史，用于支持GLUE的版本回溯功能；</span>&#x000A;<span id="LC7" class="line">- xxl_job_registry：执行器注册表，维护在线的执行器和调度中心机器地址信息；</span>&#x000A;<span id="LC8" class="line">- xxl_job_user：系统用户表；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-53-架构设计" class="anchor" href="#53-%E6%9E%B6%E6%9E%84%E8%AE%BE%E8%AE%A1"></a>5.3 架构设计</h3>&#x000A;<h4>&#x000A;<a id="user-content-531-设计思想" class="anchor" href="#531-%E8%AE%BE%E8%AE%A1%E6%80%9D%E6%83%B3"></a>5.3.1 设计思想</h4>&#x000A;<p>将调度行为抽象形成“调度中心”公共平台，而平台自身并不承担业务逻辑，“调度中心”负责发起调度请求。</p>&#x000A;<p>将任务抽象成分散的JobHandler，交由“执行器”统一管理，“执行器”负责接收调度请求并执行对应的JobHandler中业务逻辑。</p>&#x000A;<p>因此，“调度”和“任务”两部分可以相互解耦，提高系统整体稳定性和扩展性；</p>&#x000A;<h4>&#x000A;<a id="user-content-532-系统组成" class="anchor" href="#532-%E7%B3%BB%E7%BB%9F%E7%BB%84%E6%88%90"></a>5.3.2 系统组成</h4>&#x000A;<ul>&#x000A;<li>&#x000A;<strong>调度模块（调度中心）</strong>：&#x000A;负责管理调度信息，按照调度配置发出调度请求，自身不承担业务代码。调度系统与任务解耦，提高了系统可用性和稳定性，同时调度系统性能不再受限于任务模块；&#x000A;支持可视化、简单且动态的管理调度信息，包括任务新建，更新，删除，GLUE开发和任务报警等，所有上述操作都会实时生效，同时支持监控调度结果以及执行日志，支持执行器Failover。</li>&#x000A;<li>&#x000A;<strong>执行模块（执行器）</strong>：&#x000A;负责接收调度请求并执行任务逻辑。任务模块专注于任务的执行等操作，开发和维护更加简单和高效；&#x000A;接收“调度中心”的执行请求、终止请求和日志请求等。</li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-533-架构图" class="anchor" href="#533-%E6%9E%B6%E6%9E%84%E5%9B%BE"></a>5.3.3 架构图</h4>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Qohm.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h3>&#x000A;<a id="user-content-54-调度模块剖析" class="anchor" href="#54-%E8%B0%83%E5%BA%A6%E6%A8%A1%E5%9D%97%E5%89%96%E6%9E%90"></a>5.4 调度模块剖析</h3>&#x000A;<h4>&#x000A;<a id="user-content-541-quartz的不足" class="anchor" href="#541-quartz%E7%9A%84%E4%B8%8D%E8%B6%B3"></a>5.4.1 quartz的不足</h4>&#x000A;<p>Quartz作为开源作业调度中的佼佼者，是作业调度的首选。但是集群环境中Quartz采用API的方式对任务进行管理，从而可以避免上述问题，但是同样存在以下问题：</p>&#x000A;<ul>&#x000A;<li>问题一：调用API的的方式操作任务，不人性化；</li>&#x000A;<li>问题二：需要持久化业务QuartzJobBean到底层数据表中，系统侵入性相当严重。</li>&#x000A;<li>问题三：调度逻辑和QuartzJobBean耦合在同一个项目中，这将导致一个问题，在调度任务数量逐渐增多，同时调度任务逻辑逐渐加重的情况下，此时调度系统的性能将大大受限于业务；</li>&#x000A;<li>问题四：quartz底层以“抢占式”获取DB锁并由抢占成功节点负责运行任务，会导致节点负载悬殊非常大；而XXL-JOB通过执行器实现“协同分配式”运行任务，充分发挥集群优势，负载各节点均衡。</li>&#x000A;</ul>&#x000A;<p>XXL-JOB弥补了quartz的上述不足之处。</p>&#x000A;<h4>&#x000A;<a id="user-content-542-自研调度模块" class="anchor" href="#542-%E8%87%AA%E7%A0%94%E8%B0%83%E5%BA%A6%E6%A8%A1%E5%9D%97"></a>5.4.2 自研调度模块</h4>&#x000A;<p>XXL-JOB最终选择自研调度组件（早期调度组件基于Quartz）；一方面是为了精简系统降低冗余依赖，另一方面是为了提供系统的可控度与稳定性；</p>&#x000A;<p>XXL-JOB中“调度模块”和“任务模块”完全解耦，调度模块进行任务调度时，将会解析不同的任务参数发起远程调用，调用各自的远程执行器服务。这种调用模型类似RPC调用，调度中心提供调用代理的功能，而执行器提供远程服务的功能。</p>&#x000A;<h4>&#x000A;<a id="user-content-543-调度中心ha集群" class="anchor" href="#543-%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83ha%E9%9B%86%E7%BE%A4"></a>5.4.3 调度中心HA（集群）</h4>&#x000A;<p>基于数据库的集群方案，数据库选用Mysql；集群分布式并发环境中进行定时任务调度时，会在各个节点会上报任务，存到数据库中，执行时会从数据库中取出触发器来执行，如果触发器的名称和执行时间相同，则只有一个节点去执行此任务。</p>&#x000A;<h4>&#x000A;<a id="user-content-544-调度线程池" class="anchor" href="#544-%E8%B0%83%E5%BA%A6%E7%BA%BF%E7%A8%8B%E6%B1%A0"></a>5.4.4 调度线程池</h4>&#x000A;<p>调度采用线程池方式实现，避免单线程因阻塞而引起任务调度延迟。</p>&#x000A;<h4>&#x000A;<a id="user-content-545-并行调度" class="anchor" href="#545-%E5%B9%B6%E8%A1%8C%E8%B0%83%E5%BA%A6"></a>5.4.5 并行调度</h4>&#x000A;<p>XXL-JOB调度模块默认采用并行机制，在多线程调度的情况下，调度模块被阻塞的几率很低，大大提高了调度系统的承载量。</p>&#x000A;<p>XXL-JOB的不同任务之间并行调度、并行执行。&#x000A;XXL-JOB的单个任务，针对多个执行器是并行运行的，针对单个执行器是串行执行的。同时支持任务终止。</p>&#x000A;<h4>&#x000A;<a id="user-content-546-过期处理策略" class="anchor" href="#546-%E8%BF%87%E6%9C%9F%E5%A4%84%E7%90%86%E7%AD%96%E7%95%A5"></a>5.4.6 过期处理策略</h4>&#x000A;<p>任务调度错过触发时间时的处理策略：</p>&#x000A;<ul>&#x000A;<li>可能原因：服务重启；调度线程被阻塞，线程被耗尽；上次调度持续阻塞，下次调度被错过；</li>&#x000A;<li>处理策略：&#x000A;<ul>&#x000A;<li>过期超5s：本次忽略，当前时间开始计算下次触发时间</li>&#x000A;<li>过期5s内：立即触发一次，当前时间开始计算下次触发时间</li>&#x000A;</ul>&#x000A;</li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-547-日志回调服务" class="anchor" href="#547-%E6%97%A5%E5%BF%97%E5%9B%9E%E8%B0%83%E6%9C%8D%E5%8A%A1"></a>5.4.7 日志回调服务</h4>&#x000A;<p>调度模块的“调度中心”作为Web服务部署时，一方面承担调度中心功能，另一方面也为执行器提供API服务。</p>&#x000A;<p>调度中心提供的"日志回调服务API服务"代码位置如下：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">xxl-job-admin#com.xxl.job.admin.controller.JobApiController.callback</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>“执行器”在接收到任务执行请求后，执行任务，在执行结束之后会将执行结果回调通知“调度中心”：</p>&#x000A;<h4>&#x000A;<a id="user-content-548-任务hafailover" class="anchor" href="#548-%E4%BB%BB%E5%8A%A1hafailover"></a>5.4.8 任务HA（Failover）</h4>&#x000A;<p>执行器如若集群部署，调度中心将会感知到在线的所有执行器，如“127.0.0.1:9997, 127.0.0.1:9998, 127.0.0.1:9999”。</p>&#x000A;<p>当任务"路由策略"选择"故障转移(FAILOVER)"时，当调度中心每次发起调度请求时，会按照顺序对执行器发出心跳检测请求，第一个检测为存活状态的执行器将会被选定并发送调度请求。</p>&#x000A;<p>调度成功后，可在日志监控界面查看“调度备注”，如下；&#x000A;<img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_jrdI.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p>“调度备注”可以看出本地调度运行轨迹，执行器的"注册方式"、"地址列表"和任务的"路由策略"。"故障转移(FAILOVER)"路由策略下，调度中心首先对第一个地址进行心跳检测，心跳失败因此自动跳过，第二个依然心跳检测失败……&#x000A;直至心跳检测第三个地址“127.0.0.1:9999”成功，选定为“目标执行器”；然后对“目标执行器”发送调度请求，调度流程结束，等待执行器回调执行结果。</p>&#x000A;<h4>&#x000A;<a id="user-content-549-调度日志" class="anchor" href="#549-%E8%B0%83%E5%BA%A6%E6%97%A5%E5%BF%97"></a>5.4.9 调度日志</h4>&#x000A;<p>调度中心每次进行任务调度，都会记录一条任务日志，任务日志主要包括以下三部分内容：</p>&#x000A;<ul>&#x000A;<li>任务信息：包括“执行器地址”、“JobHandler”和“执行参数”等属性，点击任务ID按钮可查看，根据这些参数，可以精确的定位任务执行的具体机器和任务代码；</li>&#x000A;<li>调度信息：包括“调度时间”、“调度结果”和“调度日志”等，根据这些参数，可以了解“调度中心”发起调度请求时具体情况。</li>&#x000A;<li>执行信息：包括“执行时间”、“执行结果”和“执行日志”等，根据这些参数，可以了解在“执行器”端任务执行的具体情况；</li>&#x000A;</ul>&#x000A;<p>调度日志，针对单次调度，属性说明如下：</p>&#x000A;<ul>&#x000A;<li>执行器地址：任务执行的机器地址；</li>&#x000A;<li>JobHandler：Bean模式表示任务执行的JobHandler名称；</li>&#x000A;<li>任务参数：任务执行的入参；</li>&#x000A;<li>调度时间：调度中心，发起调度的时间；</li>&#x000A;<li>调度结果：调度中心，发起调度的结果，SUCCESS或FAIL；</li>&#x000A;<li>调度备注：调度中心，发起调度的备注信息，如地址心跳检测日志等；</li>&#x000A;<li>执行时间：执行器，任务执行结束后回调的时间；</li>&#x000A;<li>执行结果：执行器，任务执行的结果，SUCCESS或FAIL；</li>&#x000A;<li>执行备注：执行器，任务执行的备注信息，如异常日志等；</li>&#x000A;<li>执行日志：任务执行过程中，业务代码中打印的完整执行日志，见“4.8 查看执行日志”；</li>&#x000A;</ul>&#x000A;<h4>&#x000A;<a id="user-content-5410-任务依赖" class="anchor" href="#5410-%E4%BB%BB%E5%8A%A1%E4%BE%9D%E8%B5%96"></a>5.4.10 任务依赖</h4>&#x000A;<p>原理：XXL-JOB中每个任务都对应有一个任务ID，同时，每个任务支持设置属性“子任务ID”，因此，通过“任务ID”可以匹配任务依赖关系。</p>&#x000A;<p>当父任务执行结束并且执行成功时，将会根据“子任务ID”匹配子任务依赖，如果匹配到子任务，将会主动触发一次子任务的执行。</p>&#x000A;<p>在任务日志界面，点击任务的“执行备注”的“查看”按钮，可以看到匹配子任务以及触发子任务执行的日志信息，如无信息则表示未触发子任务执行，可参考下图。</p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_Wb2o.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<p><img src="https://www.xuxueli.com/doc/static/xxl-job/images/img_jOAU.png" alt="输入图片说明" title="在这里输入图片标题"></p>&#x000A;<h4>&#x000A;<a id="user-content-5411--全异步化--轻量级" class="anchor" href="#5411--%E5%85%A8%E5%BC%82%E6%AD%A5%E5%8C%96--%E8%BD%BB%E9%87%8F%E7%BA%A7"></a>5.4.11  全异步化 &amp; 轻量级</h4>&#x000A;<ul>&#x000A;<li>全异步化设计：XXL-JOB系统中业务逻辑在远程执行器执行，触发流程全异步化设计。相比直接在调度中心内部执行业务逻辑，极大的降低了调度线程占用时间；&#x000A;<ul>&#x000A;<li>异步调度：调度中心每次任务触发时仅发送一次调度请求，该调度请求首先推送“异步调度队列”，然后异步推送给远程执行器</li>&#x000A;<li>异步执行：执行器会将请求存入“异步执行队列”并且立即响应调度中心，异步运行。</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>轻量级设计：XXL-JOB调度中心中每个JOB逻辑非常 “轻”，在全异步化的基础上，单个JOB一次运行平均耗时基本在 "10ms" 之内（基本为一次请求的网络开销）；因此，可以保证使用有限的线程支撑大量的JOB并发运行；</li>&#x000A;</ul>&#x000A;<p>得益于上述两点优化，理论上默认配置下的调度中心，单机能够支撑 5000 任务并发运行稳定运行；</p>&#x000A;<p>实际场景中，由于调度中心与执行器网络ping延迟不同、DB读写耗时不同、任务调度密集程度不同，会导致任务量上限会上下波动。</p>&#x000A;<p>如若需要支撑更多的任务量，可以通过 "调大调度线程数" 、"降低调度中心与执行器ping延迟" 和 "提升机器配置" 几种方式优化。</p>&#x000A;<h4>&#x000A;<a id="user-content-5412-均衡调度" class="anchor" href="#5412-%E5%9D%87%E8%A1%A1%E8%B0%83%E5%BA%A6"></a>5.4.12 均衡调度</h4>&#x000A;<p>调度中心在集群部署时会自动进行任务平均分配，触发组件每次获取与线程池数量（调度中心支持自定义调度线程池大小）相关数量的任务，避免大量任务集中在单个调度中心集群节点；</p>&#x000A;<h3>&#x000A;<a id="user-content-55-任务-运行模式-剖析" class="anchor" href="#55-%E4%BB%BB%E5%8A%A1-%E8%BF%90%E8%A1%8C%E6%A8%A1%E5%BC%8F-%E5%89%96%E6%9E%90"></a>5.5 任务 "运行模式" 剖析</h3>&#x000A;<h4>&#x000A;<a id="user-content-551-bean模式-任务" class="anchor" href="#551-bean%E6%A8%A1%E5%BC%8F-%E4%BB%BB%E5%8A%A1"></a>5.5.1 "Bean模式" 任务</h4>&#x000A;<p>开发步骤：可参考 "章节三" ；&#x000A;原理：每个Bean模式任务都是一个Spring的Bean类实例，它被维护在“执行器”项目的Spring容器中。任务类需要加“@JobHandler(value="名称")”注解，因为“执行器”会根据该注解识别Spring容器中的任务。任务类需要继承统一接口“IJobHandler”，任务逻辑在execute方法中开发，因为“执行器”在接收到调度中心的调度请求时，将会调用“IJobHandler”的execute方法，执行任务逻辑。</p>&#x000A;<h4>&#x000A;<a id="user-content-552-glue模式java-任务" class="anchor" href="#552-glue%E6%A8%A1%E5%BC%8Fjava-%E4%BB%BB%E5%8A%A1"></a>5.5.2 "GLUE模式(Java)" 任务</h4>&#x000A;<p>开发步骤：可参考 "章节三" ；&#x000A;原理：每个 "GLUE模式(Java)" 任务的代码，实际上是“一个继承自“IJobHandler”的实现类的类代码”，“执行器”接收到“调度中心”的调度请求时，会通过Groovy类加载器加载此代码，实例化成Java对象，同时注入此代码中声明的Spring服务（请确保Glue代码中的服务和类引用在“执行器”项目中存在），然后调用该对象的execute方法，执行任务逻辑。</p>&#x000A;<h4>&#x000A;<a id="user-content-553-glue模式shell--glue模式python--glue模式php--glue模式nodejs--glue模式powershell" class="anchor" href="#553-glue%E6%A8%A1%E5%BC%8Fshell--glue%E6%A8%A1%E5%BC%8Fpython--glue%E6%A8%A1%E5%BC%8Fphp--glue%E6%A8%A1%E5%BC%8Fnodejs--glue%E6%A8%A1%E5%BC%8Fpowershell"></a>5.5.3 GLUE模式(Shell) + GLUE模式(Python) + GLUE模式(PHP) + GLUE模式(NodeJS) + GLUE模式(Powershell)</h4>&#x000A;<p>开发步骤：可参考 "章节三" ；&#x000A;原理：脚本任务的源码托管在调度中心，脚本逻辑在执行器运行。当触发脚本任务时，执行器会加载脚本源码在执行器机器上生成一份脚本文件，然后通过Java代码调用该脚本；并且实时将脚本输出日志写到任务日志文件中，从而在调度中心可以实时监控脚本运行情况；</p>&#x000A;<p>目前支持的脚本类型如下：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">- shell脚本：任务运行模式选择为 "GLUE模式(Shell)"时支持 "Shell" 脚本任务；</span>&#x000A;<span id="LC2" class="line">- python脚本：任务运行模式选择为 "GLUE模式(Python)"时支持 "Python" 脚本任务；</span>&#x000A;<span id="LC3" class="line">- php脚本：任务运行模式选择为 "GLUE模式(PHP)"时支持 "PHP" 脚本任务；</span>&#x000A;<span id="LC4" class="line">- nodejs脚本：任务运行模式选择为 "GLUE模式(NodeJS)"时支持 "NodeJS" 脚本任务；</span>&#x000A;<span id="LC5" class="line">- powershell：任务运行模式选择为 "GLUE模式(PowerShell)"时支持 "PowerShell" 脚本任务；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>脚本任务通过 Exit Code 判断任务执行结果，状态码可参考章节 "5.15 任务执行结果说明"；</p>&#x000A;<h4>&#x000A;<a id="user-content-554-执行器" class="anchor" href="#554-%E6%89%A7%E8%A1%8C%E5%99%A8"></a>5.5.4 执行器</h4>&#x000A;<p>执行器实际上是一个内嵌的Server，默认端口9999（配置项：xxl.job.executor.port）。</p>&#x000A;<p>在项目启动时，执行器会通过“@JobHandler”识别Spring容器中“Bean模式任务”，以注解的value属性为key管理起来。</p>&#x000A;<p>“执行器”接收到“调度中心”的调度请求时，如果任务类型为“Bean模式”，将会匹配Spring容器中的“Bean模式任务”，然后调用其execute方法，执行任务逻辑。如果任务类型为“GLUE模式”，将会加载GLue代码，实例化Java对象，注入依赖的Spring服务（注意：Glue代码中注入的Spring服务，必须存在与该“执行器”项目的Spring容器中），然后调用execute方法，执行任务逻辑。</p>&#x000A;<h4>&#x000A;<a id="user-content-555-任务日志" class="anchor" href="#555-%E4%BB%BB%E5%8A%A1%E6%97%A5%E5%BF%97"></a>5.5.5 任务日志</h4>&#x000A;<p>XXL-JOB会为每次调度请求生成一个单独的日志文件，需要通过 "XxlJobHelper.log" 打印执行日志，“调度中心”查看执行日志时将会加载对应的日志文件。</p>&#x000A;<p>(历史版本通过重写LOG4J的Appender实现，存在依赖限制，该方式在新版本已经被抛弃)</p>&#x000A;<p>日志文件存放的位置可在“执行器”配置文件进行自定义，默认目录格式为：/data/applogs/xxl-job/jobhandler/“格式化日期”/“数据库调度日志记录的主键ID.log”。</p>&#x000A;<p>在JobHandler中开启子线程时，子线程将会将会把日志打印在父线程即JobHandler的执行日志中，方便日志追踪。</p>&#x000A;<h3>&#x000A;<a id="user-content-56-通讯模块剖析" class="anchor" href="#56-%E9%80%9A%E8%AE%AF%E6%A8%A1%E5%9D%97%E5%89%96%E6%9E%90"></a>5.6 通讯模块剖析</h3>&#x000A;<h4>&#x000A;<a id="user-content-561-一次完整的任务调度通讯流程" class="anchor" href="#561-%E4%B8%80%E6%AC%A1%E5%AE%8C%E6%95%B4%E7%9A%84%E4%BB%BB%E5%8A%A1%E8%B0%83%E5%BA%A6%E9%80%9A%E8%AE%AF%E6%B5%81%E7%A8%8B"></a>5.6.1 一次完整的任务调度通讯流程</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">- 1、“调度中心”向“执行器”发送http调度请求: “执行器”中接收请求的服务，实际上是一台内嵌Server，默认端口9999;</span>&#x000A;<span id="LC2" class="line">- 2、“执行器”执行任务逻辑；</span>&#x000A;<span id="LC3" class="line">- 3、“执行器”http回调“调度中心”调度结果: “调度中心”中接收回调的服务，是针对执行器开放一套API服务;</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-562-通讯数据加密" class="anchor" href="#562-%E9%80%9A%E8%AE%AF%E6%95%B0%E6%8D%AE%E5%8A%A0%E5%AF%86"></a>5.6.2 通讯数据加密</h4>&#x000A;<p>调度中心向执行器发送的调度请求时使用RequestModel和ResponseModel两个对象封装调度请求参数和响应数据, 在进行通讯之前底层会将上述两个对象对象序列化，并进行数据协议以及时间戳检验,从而达到数据加密的功能;</p>&#x000A;<h3>&#x000A;<a id="user-content-57-任务注册-任务自动发现" class="anchor" href="#57-%E4%BB%BB%E5%8A%A1%E6%B3%A8%E5%86%8C-%E4%BB%BB%E5%8A%A1%E8%87%AA%E5%8A%A8%E5%8F%91%E7%8E%B0"></a>5.7 任务注册, 任务自动发现</h3>&#x000A;<p>自v1.5版本之后, 任务取消了"任务执行机器"属性, 改为通过任务注册和自动发现的方式, 动态获取远程执行器地址并执行。</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">AppName: 每个执行器机器集群的唯一标示, 任务注册以 "执行器" 为最小粒度进行注册; 每个任务通过其绑定的执行器可感知对应的执行器机器列表;</span>&#x000A;<span id="LC2" class="line">注册表: 见"xxl_job_registry"表, "执行器" 在进行任务注册时将会周期性维护一条注册记录，即机器地址和AppName的绑定关系; "调度中心" 从而可以动态感知每个AppName在线的机器列表;</span>&#x000A;<span id="LC3" class="line">执行器注册: 任务注册Beat周期默认30s; 执行器以一倍Beat进行执行器注册, 调度中心以一倍Beat进行动态任务发现; 注册信息的失效时间为三倍Beat; </span>&#x000A;<span id="LC4" class="line">执行器注册摘除：执行器销毁时，将会主动上报调度中心并摘除对应的执行器机器信息，提高心跳注册的实时性；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>为保证系统"轻量级"并且降低学习部署成本，没有采用Zookeeper作为注册中心，采用DB方式进行任务注册发现；</p>&#x000A;<h3>&#x000A;<a id="user-content-58-任务执行结果" class="anchor" href="#58-%E4%BB%BB%E5%8A%A1%E6%89%A7%E8%A1%8C%E7%BB%93%E6%9E%9C"></a>5.8 任务执行结果</h3>&#x000A;<p>自v1.6.2之后，任务执行结果通过 "IJobHandler" 的返回值 "ReturnT" 进行判断；&#x000A;当返回值符合 "ReturnT.code == ReturnT.SUCCESS_CODE" 时表示任务执行成功，否则表示任务执行失败，而且可以通过 "ReturnT.msg" 回调错误信息给调度中心；&#x000A;从而，在任务逻辑中可以方便的控制任务执行结果；</p>&#x000A;<h3>&#x000A;<a id="user-content-59-分片广播--动态分片" class="anchor" href="#59-%E5%88%86%E7%89%87%E5%B9%BF%E6%92%AD--%E5%8A%A8%E6%80%81%E5%88%86%E7%89%87"></a>5.9 分片广播 &amp; 动态分片</h3>&#x000A;<p>执行器集群部署时，任务路由策略选择"分片广播"情况下，一次任务调度将会广播触发对应集群中所有执行器执行一次任务，同时系统自动传递分片参数；可根据分片参数开发分片任务；</p>&#x000A;<p>"分片广播" 以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。</p>&#x000A;<p>"分片广播" 和普通任务开发流程一致，不同之处在于可以获取分片参数，获取分片参数进行分片业务处理。</p>&#x000A;<ul>&#x000A;<li>Java语言任务获取分片参数方式：BEAN、GLUE模式(Java)</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">// 可参考Sample示例执行器中的示例任务"ShardingJobHandler"了解试用 </span>&#x000A;<span id="LC2" class="line">int shardIndex = XxlJobHelper.getShardIndex();</span>&#x000A;<span id="LC3" class="line">int shardTotal = XxlJobHelper.getShardTotal();</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<ul>&#x000A;<li>脚本语言任务获取分片参数方式：GLUE模式(Shell)、GLUE模式(Python)、GLUE模式(Nodejs)</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">// 脚本任务入参固定为三个，依次为：任务传参、分片序号、分片总数。以Shell模式任务为例，获取分片参数代码如下</span>&#x000A;<span id="LC2" class="line">echo "分片序号 index = $2"</span>&#x000A;<span id="LC3" class="line">echo "分片总数 total = $3"</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>分片参数属性说明：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">index：当前分片序号(从0开始)，执行器集群列表中当前执行器的序号；</span>&#x000A;<span id="LC2" class="line">total：总分片数，执行器集群的总机器数量；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>该特性适用场景如：</p>&#x000A;<ul>&#x000A;<li>1、分片任务场景：10个执行器的集群来处理10w条数据，每台机器只需要处理1w条数据，耗时降低10倍；</li>&#x000A;<li>2、广播任务场景：广播执行器机器运行shell脚本、广播集群节点进行缓存更新等</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-510-访问令牌accesstoken" class="anchor" href="#510-%E8%AE%BF%E9%97%AE%E4%BB%A4%E7%89%8Caccesstoken"></a>5.10 访问令牌（AccessToken）</h3>&#x000A;<p>为提升系统安全性，调度中心和执行器进行安全性校验，双方AccessToken匹配才允许通讯；</p>&#x000A;<p>调度中心和执行器，可通过配置项 "xxl.job.accessToken" 进行AccessToken的设置。</p>&#x000A;<p>调度中心和执行器，如果需要正常通讯，只有两种设置；</p>&#x000A;<ul>&#x000A;<li>设置一：调度中心和执行器，均不设置AccessToken；关闭安全性校验；</li>&#x000A;<li>设置二：调度中心和执行器，设置了相同的AccessToken；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-511-故障转移--失败重试" class="anchor" href="#511-%E6%95%85%E9%9A%9C%E8%BD%AC%E7%A7%BB--%E5%A4%B1%E8%B4%A5%E9%87%8D%E8%AF%95"></a>5.11 故障转移 &amp; 失败重试</h3>&#x000A;<p>一次完整任务流程包括"调度（调度中心） + 执行（执行器）"两个阶段。</p>&#x000A;<ul>&#x000A;<li>"故障转移"发生在调度阶段，在执行器集群部署时，如果某一台执行器发生故障，该策略支持自动进行Failover切换到一台正常的执行器机器并且完成调度请求流程。</li>&#x000A;<li>"失败重试"发生在"调度 + 执行"两个阶段，支持通过自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-512-执行器灰度上线" class="anchor" href="#512-%E6%89%A7%E8%A1%8C%E5%99%A8%E7%81%B0%E5%BA%A6%E4%B8%8A%E7%BA%BF"></a>5.12 执行器灰度上线</h3>&#x000A;<p>调度中心与业务解耦，只需部署一次后常年不需要维护。但是，执行器中托管运行着业务作业，作业上线和变更需要重启执行器，尤其是Bean模式任务。&#x000A;执行器重启可能会中断运行中的任务。但是，XXL-JOB得益于自建执行器与自建注册中心，可以通过灰度上线的方式，避免因重启导致的任务中断的问题。</p>&#x000A;<p>步骤如下：</p>&#x000A;<ul>&#x000A;<li>1、执行器改为手动注册，下线一半机器列表（A组），线上运行另一半机器列表（B组）；</li>&#x000A;<li>2、等待A组机器任务运行结束并编译上线；执行器注册地址替换为A组；</li>&#x000A;<li>3、等待B组机器任务运行结束并编译上线；执行器注册地址替换为A组+B组；&#x000A;操作结束；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-513-任务执行结果说明" class="anchor" href="#513-%E4%BB%BB%E5%8A%A1%E6%89%A7%E8%A1%8C%E7%BB%93%E6%9E%9C%E8%AF%B4%E6%98%8E"></a>5.13 任务执行结果说明</h3>&#x000A;<p>系统根据以下标准判断任务执行结果，可参考之。</p>&#x000A;<table>&#x000A;<thead>&#x000A;<tr>&#x000A;<th>--</th>&#x000A;<th>Bean/Glue(Java)</th>&#x000A;<th>Glue(Shell) 等脚本任务</th>&#x000A;</tr>&#x000A;</thead>&#x000A;<tbody>&#x000A;<tr>&#x000A;<td>成功</td>&#x000A;<td>IJobHandler.SUCCESS</td>&#x000A;<td>0</td>&#x000A;</tr>&#x000A;<tr>&#x000A;<td>失败</td>&#x000A;<td>IJobHandler.FAIL</td>&#x000A;<td>-1（非0状态码）</td>&#x000A;</tr>&#x000A;</tbody>&#x000A;</table>&#x000A;<h3>&#x000A;<a id="user-content-514-任务超时控制" class="anchor" href="#514-%E4%BB%BB%E5%8A%A1%E8%B6%85%E6%97%B6%E6%8E%A7%E5%88%B6"></a>5.14 任务超时控制</h3>&#x000A;<p>支持设置任务超时时间，任务运行超时的情况下，将会主动中断任务；</p>&#x000A;<p>需要注意的是，任务超时中断时与任务终止机制（可查看“4.9 终止运行中的任务”）类似，也是通过 "interrupt" 中断任务，因此业务代码需要将 "InterruptedException" 外抛，否则功能不可用。</p>&#x000A;<h3>&#x000A;<a id="user-content-515-跨语言" class="anchor" href="#515-%E8%B7%A8%E8%AF%AD%E8%A8%80"></a>5.15 跨语言</h3>&#x000A;<p>XXL-JOB是一个跨语言的任务调度平台，主要体现在如下几个方面：</p>&#x000A;<ul>&#x000A;<li>1、RESTful API：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。（可参考章节 “调度中心/执行器 RESTful API” ）</li>&#x000A;<li>2、多任务模式：提供Java、Python、PHP……等十来种任务模式，可参考章节 “5.5 任务 "运行模式" ”；理论上可扩展任意语言任务模式；</li>&#x000A;<li>2、提供基于HTTP的任务Handler（Bean任务，JobHandler="httpJobHandler"）；业务方只需要提供HTTP链接等相关信息即可，不限制语言、平台；（可参考章节 “原生内置Bean模式任务” ）</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-516-任务失败告警" class="anchor" href="#516-%E4%BB%BB%E5%8A%A1%E5%A4%B1%E8%B4%A5%E5%91%8A%E8%AD%A6"></a>5.16 任务失败告警</h3>&#x000A;<p>默认提供邮件失败告警，可扩展短信、钉钉等方式。如果需要新增一种告警方式，只需要新增一个实现 "com.xxl.job.admin.core.alarm.JobAlarm" 接口的告警实现即可。可以参考默认提供邮箱告警实现 "EmailJobAlarm"。</p>&#x000A;<h3>&#x000A;<a id="user-content-517-调度中心docker镜像构建" class="anchor" href="#517-%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83docker%E9%95%9C%E5%83%8F%E6%9E%84%E5%BB%BA"></a>5.17 调度中心Docker镜像构建</h3>&#x000A;<p>可以通过以下命令快速构建调度中心，并启动运行；</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">mvn clean package</span>&#x000A;<span id="LC2" class="line">docker build -t xuxueli/xxl-job-admin ./xxl-job-admin</span>&#x000A;<span id="LC3" class="line">docker run --name xxl-job-admin -p 8080:8080 -d xuxueli/xxl-job-admin</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-520-避免任务重复执行" class="anchor" href="#520-%E9%81%BF%E5%85%8D%E4%BB%BB%E5%8A%A1%E9%87%8D%E5%A4%8D%E6%89%A7%E8%A1%8C"></a>5.20 避免任务重复执行</h3>&#x000A;<p>调度密集或者耗时任务可能会导致任务阻塞，集群情况下调度组件小概率情况下会重复触发；&#x000A;针对上述情况，可以通过结合 "单机路由策略（如：第一台、一致性哈希）" + "阻塞策略（如：单机串行、丢弃后续调度）" 来规避，最终避免任务重复执行。</p>&#x000A;<h3>&#x000A;<a id="user-content-521-命令行任务" class="anchor" href="#521-%E5%91%BD%E4%BB%A4%E8%A1%8C%E4%BB%BB%E5%8A%A1"></a>5.21 命令行任务</h3>&#x000A;<p>原生提供通用命令行任务Handler（Bean任务，"CommandJobHandler"）；业务方只需要提供命令行即可；&#x000A;如任务参数 "pwd" 将会执行命令并输出数据；</p>&#x000A;<h3>&#x000A;<a id="user-content-522-日志自动清理" class="anchor" href="#522-%E6%97%A5%E5%BF%97%E8%87%AA%E5%8A%A8%E6%B8%85%E7%90%86"></a>5.22 日志自动清理</h3>&#x000A;<p>XXL-JOB日志主要包含如下两部分，均支持日志自动清理，说明如下：</p>&#x000A;<ul>&#x000A;<li>调度中心日志表数据：可借助配置项 "xxl.job.logretentiondays" 设置日志表数据保存天数，过期日志自动清理；详情可查看上文配置说明；</li>&#x000A;<li>执行器日志文件数据：可借助配置项 "xxl.job.executor.logretentiondays" 设置日志文件数据保存天数，过期日志自动清理；详情可查看上文配置说明；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-523-调度结果丢失处理" class="anchor" href="#523-%E8%B0%83%E5%BA%A6%E7%BB%93%E6%9E%9C%E4%B8%A2%E5%A4%B1%E5%A4%84%E7%90%86"></a>5.23 调度结果丢失处理</h3>&#x000A;<p>执行器因网络抖动回调失败或宕机等异常情况，会导致任务调度结果丢失。由于调度中心依赖执行器回调来感知调度结果，因此会导致调度日志永远处于 "运行中" 状态。</p>&#x000A;<p>针对该问题，调度中心提供内置组件进行处理，逻辑为：调度记录停留在 "运行中" 状态超过10min，且对应执行器心跳注册失败不在线，则将本地调度主动标记失败；</p>&#x000A;<h2>&#x000A;<a id="user-content-六调度中心执行器-restful-api" class="anchor" href="#%E5%85%AD%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83%E6%89%A7%E8%A1%8C%E5%99%A8-restful-api"></a>六、调度中心/执行器 RESTful API</h2>&#x000A;<p>XXL-JOB 目标是一种跨平台、跨语言的任务调度规范和协议。</p>&#x000A;<p>针对Java应用，可以直接通过官方提供的调度中心与执行器，方便快速的接入和使用调度中心，可以参考上文 “快速入门” 章节。</p>&#x000A;<p>针对非Java应用，可借助 XXL-JOB 的标准 RESTful API 方便的实现多语言支持。</p>&#x000A;<ul>&#x000A;<li>调度中心 RESTful API：&#x000A;<ul>&#x000A;<li>说明：调度中心提供给执行器使用的API；不局限于官方执行器使用，第三方可使用该API来实现执行器；</li>&#x000A;<li>API列表：执行器注册、任务结果回调等；</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>执行器 RESTful API ：&#x000A;<ul>&#x000A;<li>说明：执行器提供给调度中心使用的API；官方执行器默认已实现，第三方执行器需要实现并对接提供给调度中心；</li>&#x000A;<li>API列表：任务触发、任务终止、任务日志查询……等；</li>&#x000A;</ul>&#x000A;</li>&#x000A;</ul>&#x000A;<p>此处 RESTful API 主要用于非Java语言定制个性化执行器使用，实现跨语言。除此之外，如果有需要通过API操作调度中心，可以个性化扩展 “调度中心 RESTful API” 并使用。</p>&#x000A;<h3>&#x000A;<a id="user-content-61-调度中心-restful-api" class="anchor" href="#61-%E8%B0%83%E5%BA%A6%E4%B8%AD%E5%BF%83-restful-api"></a>6.1 调度中心 RESTful API</h3>&#x000A;<p>API服务位置：com.xxl.job.core.biz.AdminBiz （ com.xxl.job.admin.controller.JobApiController ）&#x000A;API服务请求参考代码：com.xxl.job.adminbiz.AdminBizTest</p>&#x000A;<h4>&#x000A;<a id="user-content-a任务回调" class="anchor" href="#a%E4%BB%BB%E5%8A%A1%E5%9B%9E%E8%B0%83"></a>a、任务回调</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：执行器执行完任务后，回调任务结果时使用</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{调度中心根地址}/api/callback</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    [{</span>&#x000A;<span id="LC12" class="line">        "logId":1,              // 本次调度日志ID</span>&#x000A;<span id="LC13" class="line">        "logDateTim":0,         // 本次调度日志时间</span>&#x000A;<span id="LC14" class="line">        "handleCode":200,       // 200 表示任务执行正常，500表示失败</span>&#x000A;<span id="LC15" class="line">        "handleMsg": null</span>&#x000A;<span id="LC16" class="line">        }</span>&#x000A;<span id="LC17" class="line">    }]</span>&#x000A;<span id="LC18" class="line"></span>&#x000A;<span id="LC19" class="line">响应数据格式：</span>&#x000A;<span id="LC20" class="line">    {</span>&#x000A;<span id="LC21" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC22" class="line">      "msg": null      // 错误提示消息</span>&#x000A;<span id="LC23" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-b执行器注册" class="anchor" href="#b%E6%89%A7%E8%A1%8C%E5%99%A8%E6%B3%A8%E5%86%8C"></a>b、执行器注册</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：执行器注册时使用，调度中心会实时感知注册成功的执行器并发起任务调度</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{调度中心根地址}/api/registry</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "registryGroup":"EXECUTOR",                     // 固定值</span>&#x000A;<span id="LC13" class="line">        "registryKey":"xxl-job-executor-example",       // 执行器AppName</span>&#x000A;<span id="LC14" class="line">        "registryValue":"http://127.0.0.1:9999/"        // 执行器地址，内置服务跟地址</span>&#x000A;<span id="LC15" class="line">    }</span>&#x000A;<span id="LC16" class="line"></span>&#x000A;<span id="LC17" class="line">响应数据格式：</span>&#x000A;<span id="LC18" class="line">    {</span>&#x000A;<span id="LC19" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC20" class="line">      "msg": null      // 错误提示消息</span>&#x000A;<span id="LC21" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-c执行器注册摘除" class="anchor" href="#c%E6%89%A7%E8%A1%8C%E5%99%A8%E6%B3%A8%E5%86%8C%E6%91%98%E9%99%A4"></a>c、执行器注册摘除</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：执行器注册摘除时使用，注册摘除后的执行器不参与任务调度与执行</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{调度中心根地址}/api/registryRemove</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "registryGroup":"EXECUTOR",                     // 固定值</span>&#x000A;<span id="LC13" class="line">        "registryKey":"xxl-job-executor-example",       // 执行器AppName</span>&#x000A;<span id="LC14" class="line">        "registryValue":"http://127.0.0.1:9999/"        // 执行器地址，内置服务跟地址</span>&#x000A;<span id="LC15" class="line">    }</span>&#x000A;<span id="LC16" class="line"></span>&#x000A;<span id="LC17" class="line">响应数据格式：</span>&#x000A;<span id="LC18" class="line">    {</span>&#x000A;<span id="LC19" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC20" class="line">      "msg": null      // 错误提示消息</span>&#x000A;<span id="LC21" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h3>&#x000A;<a id="user-content-62-执行器-restful-api" class="anchor" href="#62-%E6%89%A7%E8%A1%8C%E5%99%A8-restful-api"></a>6.2 执行器 RESTful API</h3>&#x000A;<p>API服务位置：com.xxl.job.core.biz.ExecutorBiz&#x000A;API服务请求参考代码：com.xxl.job.executorbiz.ExecutorBizTest</p>&#x000A;<h4>&#x000A;<a id="user-content-a心跳检测" class="anchor" href="#a%E5%BF%83%E8%B7%B3%E6%A3%80%E6%B5%8B"></a>a、心跳检测</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：调度中心检测执行器是否在线时使用</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{执行器内嵌服务根地址}/beat</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line"></span>&#x000A;<span id="LC12" class="line">响应数据格式：</span>&#x000A;<span id="LC13" class="line">    {</span>&#x000A;<span id="LC14" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC15" class="line">      "msg": null       // 错误提示消息</span>&#x000A;<span id="LC16" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-b忙碌检测" class="anchor" href="#b%E5%BF%99%E7%A2%8C%E6%A3%80%E6%B5%8B"></a>b、忙碌检测</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：调度中心检测指定执行器上指定任务是否忙碌（运行中）时使用</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{执行器内嵌服务根地址}/idleBeat</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "jobId":1       // 任务ID</span>&#x000A;<span id="LC13" class="line">    }</span>&#x000A;<span id="LC14" class="line"></span>&#x000A;<span id="LC15" class="line">响应数据格式：</span>&#x000A;<span id="LC16" class="line">    {</span>&#x000A;<span id="LC17" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC18" class="line">      "msg": null       // 错误提示消息</span>&#x000A;<span id="LC19" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-c触发任务" class="anchor" href="#c%E8%A7%A6%E5%8F%91%E4%BB%BB%E5%8A%A1"></a>c、触发任务</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：触发任务执行</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{执行器内嵌服务根地址}/run</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "jobId":1,                                  // 任务ID</span>&#x000A;<span id="LC13" class="line">        "executorHandler":"demoJobHandler",         // 任务标识</span>&#x000A;<span id="LC14" class="line">        "executorParams":"demoJobHandler",          // 任务参数</span>&#x000A;<span id="LC15" class="line">        "executorBlockStrategy":"COVER_EARLY",      // 任务阻塞策略，可选值参考 com.xxl.job.core.enums.ExecutorBlockStrategyEnum</span>&#x000A;<span id="LC16" class="line">        "executorTimeout":0,                        // 任务超时时间，单位秒，大于零时生效</span>&#x000A;<span id="LC17" class="line">        "logId":1,                                  // 本次调度日志ID</span>&#x000A;<span id="LC18" class="line">        "logDateTime":1586629003729,                // 本次调度日志时间</span>&#x000A;<span id="LC19" class="line">        "glueType":"BEAN",                          // 任务模式，可选值参考 com.xxl.job.core.glue.GlueTypeEnum</span>&#x000A;<span id="LC20" class="line">        "glueSource":"xxx",                         // GLUE脚本代码</span>&#x000A;<span id="LC21" class="line">        "glueUpdatetime":1586629003727,             // GLUE脚本更新时间，用于判定脚本是否变更以及是否需要刷新</span>&#x000A;<span id="LC22" class="line">        "broadcastIndex":0,                         // 分片参数：当前分片</span>&#x000A;<span id="LC23" class="line">        "broadcastTotal":0                          // 分片参数：总分片</span>&#x000A;<span id="LC24" class="line">    }</span>&#x000A;<span id="LC25" class="line"></span>&#x000A;<span id="LC26" class="line">响应数据格式：</span>&#x000A;<span id="LC27" class="line">    {</span>&#x000A;<span id="LC28" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC29" class="line">      "msg": null       // 错误提示消息</span>&#x000A;<span id="LC30" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-f终止任务" class="anchor" href="#f%E7%BB%88%E6%AD%A2%E4%BB%BB%E5%8A%A1"></a>f、终止任务</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：终止任务</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{执行器内嵌服务根地址}/kill</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "jobId":1       // 任务ID</span>&#x000A;<span id="LC13" class="line">    }</span>&#x000A;<span id="LC14" class="line">    </span>&#x000A;<span id="LC15" class="line"></span>&#x000A;<span id="LC16" class="line">响应数据格式：</span>&#x000A;<span id="LC17" class="line">    {</span>&#x000A;<span id="LC18" class="line">      "code": 200,      // 200 表示正常、其他失败</span>&#x000A;<span id="LC19" class="line">      "msg": null       // 错误提示消息</span>&#x000A;<span id="LC20" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h4>&#x000A;<a id="user-content-d查看执行日志" class="anchor" href="#d%E6%9F%A5%E7%9C%8B%E6%89%A7%E8%A1%8C%E6%97%A5%E5%BF%97"></a>d、查看执行日志</h4>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">说明：终止任务，滚动方式加载</span>&#x000A;<span id="LC2" class="line"></span>&#x000A;<span id="LC3" class="line">------</span>&#x000A;<span id="LC4" class="line"></span>&#x000A;<span id="LC5" class="line">地址格式：{执行器内嵌服务根地址}/log</span>&#x000A;<span id="LC6" class="line"></span>&#x000A;<span id="LC7" class="line">Header：</span>&#x000A;<span id="LC8" class="line">    XXL-JOB-ACCESS-TOKEN : {请求令牌}</span>&#x000A;<span id="LC9" class="line"> </span>&#x000A;<span id="LC10" class="line">请求数据格式如下，放置在 RequestBody 中，JSON格式：</span>&#x000A;<span id="LC11" class="line">    {</span>&#x000A;<span id="LC12" class="line">        "logDateTim":0,     // 本次调度日志时间</span>&#x000A;<span id="LC13" class="line">        "logId":0,          // 本次调度日志ID</span>&#x000A;<span id="LC14" class="line">        "fromLineNum":0     // 日志开始行号，滚动加载日志</span>&#x000A;<span id="LC15" class="line">    }</span>&#x000A;<span id="LC16" class="line"></span>&#x000A;<span id="LC17" class="line">响应数据格式：</span>&#x000A;<span id="LC18" class="line">    {</span>&#x000A;<span id="LC19" class="line">        "code":200,         // 200 表示正常、其他失败</span>&#x000A;<span id="LC20" class="line">        "msg": null         // 错误提示消息</span>&#x000A;<span id="LC21" class="line">        "content":{</span>&#x000A;<span id="LC22" class="line">            "fromLineNum":0,        // 本次请求，日志开始行数</span>&#x000A;<span id="LC23" class="line">            "toLineNum":100,        // 本次请求，日志结束行号</span>&#x000A;<span id="LC24" class="line">            "logContent":"xxx",     // 本次请求日志内容</span>&#x000A;<span id="LC25" class="line">            "isEnd":true            // 日志是否全部加载完</span>&#x000A;<span id="LC26" class="line">        }</span>&#x000A;<span id="LC27" class="line">    }</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<h2>&#x000A;<a id="user-content-七版本更新日志" class="anchor" href="#%E4%B8%83%E7%89%88%E6%9C%AC%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97"></a>七、版本更新日志</h2>&#x000A;<h3>&#x000A;<a id="user-content-71-版本-v11x新特性2015-12-05" class="anchor" href="#71-%E7%89%88%E6%9C%AC-v11x%E6%96%B0%E7%89%B9%E6%80%A72015-12-05"></a>7.1 版本 V1.1.x，新特性[2015-12-05]</h3>&#x000A;<p><strong>【于V1.1.x版本，XXL-JOB正式应用于我司，内部定制别名为 “Ferrari”，新接入应用推荐使用最新版本】</strong></p>&#x000A;<ul>&#x000A;<li>1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；</li>&#x000A;<li>2、动态：支持动态修改任务状态，动态暂停/恢复任务，即时生效；</li>&#x000A;<li>3、服务HA：任务信息持久化到mysql中，Job服务天然支持集群，保证服务HA；</li>&#x000A;<li>4、任务HA：某台Job服务挂掉，任务会平滑分配给其他的某一台存活服务，即使所有服务挂掉，重启时或补偿执行丢失任务；</li>&#x000A;<li>5、一个任务只会在其中一台服务器上执行；</li>&#x000A;<li>6、任务串行执行；</li>&#x000A;<li>7、支持自定义参数；</li>&#x000A;<li>8、支持远程任务执行终止；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-72-版本-v12x新特性2016-01-17" class="anchor" href="#72-%E7%89%88%E6%9C%AC-v12x%E6%96%B0%E7%89%B9%E6%80%A72016-01-17"></a>7.2 版本 V1.2.x，新特性[2016-01-17]</h3>&#x000A;<ul>&#x000A;<li>&#x000A;<p>1、支持任务分组；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>2、支持“本地任务”、“远程任务”；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>3、底层通讯支持两种方式，Servlet方式 + JETTY方式；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>4、支持“任务日志”；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>5、支持“串行执行”，并行执行；</p>&#x000A;<p>说明：V1.2版本将系统架构按功能拆分为：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">  - 调度模块（调度中心）：负责管理调度信息，按照调度配置发出调度请求；</span>&#x000A;<span id="LC2" class="line">  - 执行模块（执行器）：负责接收调度请求并执行任务逻辑；</span>&#x000A;<span id="LC3" class="line">  - 通讯模块：负责调度模块和任务模块之间的信息通讯；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<p>优点：</p>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">  - 解耦：任务模块提供任务接口，调度模块维护调度信息，业务相互独立；</span>&#x000A;<span id="LC2" class="line">  - 高扩展性；</span>&#x000A;<span id="LC3" class="line">  - 稳定性；</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-73-版本-v130新特性2016-05-19" class="anchor" href="#73-%E7%89%88%E6%9C%AC-v130%E6%96%B0%E7%89%B9%E6%80%A72016-05-19"></a>7.3 版本 V1.3.0，新特性[2016-05-19]</h3>&#x000A;<ul>&#x000A;<li>&#x000A;<p>1、遗弃“本地任务”模式，推荐使用“远程任务”，易于系统解耦，任务对应的JobHandler统称为“执行器”；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>2、遗弃“servlet”方式底层系统通讯，推荐使用JETTY方式，调度+回调双向通讯，重构通讯逻辑；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>3、UI交互优化：左侧菜单展开状态优化，菜单项选中状态优化，任务列表打开表格有压缩优化；</p>&#x000A;</li>&#x000A;<li>&#x000A;<p>4、【重要】“执行器”细分为：BEAN、GLUE两种开发模式，简介见下文：</p>&#x000A;<p>“执行器” 模式简介：&#x000A;- BEAN模式执行器：每个执行器都是Spring的一个Bean实例，XXL-JOB通过注解@JobHandler识别和调度执行器；&#x000A;-GLUE模式执行器：每个执行器对应一段代码，在线Web编辑和维护，动态编译生效，执行器负责加载GLUE代码和执行；</p>&#x000A;</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-74-版本-v131新特性2016-05-23" class="anchor" href="#74-%E7%89%88%E6%9C%AC-v131%E6%96%B0%E7%89%B9%E6%80%A72016-05-23"></a>7.4 版本 V1.3.1，新特性[2016-05-23]</h3>&#x000A;<ul>&#x000A;<li>1、更新项目目录结构：&#x000A;<ul>&#x000A;<li>/xxl-job-admin -------------------- 【调度中心】：负责管理调度信息，按照调度配置发出调度请求；</li>&#x000A;<li>/xxl-job-core ----------------------- 公共依赖</li>&#x000A;<li>/xxl-job-executor-example ------ 【执行器】：负责接收调度请求并执行任务逻辑；</li>&#x000A;<li>/db ---------------------------------- 建表脚本</li>&#x000A;<li>/doc --------------------------------- 用户手册</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>2、在新的目录结构上，升级了用户手册；</li>&#x000A;<li>3、优化了一些交互和UI；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-75-版本-v132新特性2016-05-28" class="anchor" href="#75-%E7%89%88%E6%9C%AC-v132%E6%96%B0%E7%89%B9%E6%80%A72016-05-28"></a>7.5 版本 V1.3.2，新特性[2016-05-28]</h3>&#x000A;<ul>&#x000A;<li>1、调度逻辑进行事务包裹；</li>&#x000A;<li>2、执行器异步回调执行日志；</li>&#x000A;<li>3、【重要】在 “调度中心” 支持HA的基础上，扩展执行器的Failover支持，支持配置多执行期地址；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-76-版本-v140-新特性2016-07-24" class="anchor" href="#76-%E7%89%88%E6%9C%AC-v140-%E6%96%B0%E7%89%B9%E6%80%A72016-07-24"></a>7.6 版本 V1.4.0 新特性[2016-07-24]</h3>&#x000A;<ul>&#x000A;<li>1、任务依赖: 通过事件触发方式实现, 任务执行成功并回调时会主动触发一次子任务的调度, 多个子任务用逗号分隔;</li>&#x000A;<li>2、执行器底层实现代码进行重度重构, 优化底层建表脚本;</li>&#x000A;<li>3、执行器中任务线程分组逻辑优化: 之前根据执行器JobHandler进行线程分组,当多个任务复用Jobhanlder会导致相互阻塞。现改为根据调度中心任务进行任务线程分组,任务与任务执行相互隔离;</li>&#x000A;<li>4、执行器调度通讯方案优化, 通过Hex + HC实现建议RPC通讯协议, 优化了通讯参数的维护和解析流程;</li>&#x000A;<li>5、调度中心, 新建/编辑任务, 界面属性调整:&#x000A;<ul>&#x000A;<li>5.1、任务新增/编辑界面中去除 "任务名JobName"属性 ,该属性改为系统自动生成: 该字段之前主要用于在 "调度中心" 唯一标示一个任务, 现实意义不大, 因此计划淡化掉该字段,改为系统生成UUID,从而简化任务新建的操作;</li>&#x000A;<li>5.2、任务新增/编辑界面中去除 "GLUE模式" 复选框位置调整, 改为贴近"JobHandler"输入框右侧;</li>&#x000A;<li>5.3、任务新增/编辑界面中去除 "报警阈值" 属性;</li>&#x000A;<li>5.4、任务新增/编辑界面中去除 "子任务Key" 属性, 每个任务全局任务Key可以从任务列表获取, 当本任务执行结束且成功后, 将会根据子任务Key匹配子任务并主动触发一次子任务执行;</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>6、问题修复:&#x000A;<ul>&#x000A;<li>6.1、执行器jetty关闭优化,解决一处可能导致jetty无法关闭的问题;</li>&#x000A;<li>6.2、执行器任务终止时,执行队列回调优化,解决一处导致任务无法回调的问题；</li>&#x000A;<li>6.3、调度中心中列表分页参数优化,解决一处因服务器限制post长度而引起的问题;</li>&#x000A;<li>6.4、执行器Jobhandler注解优化,解决一处因事务代理导致的容器无法加载JobHandler的问题;</li>&#x000A;<li>6.5、远程调度优化,禁用retry策略,解决一处可能导致重复调用的问题;</li>&#x000A;</ul>&#x000A;</li>&#x000A;</ul>&#x000A;<p>Tips: 历史版本(V1.3.x)目前已经Release至稳定版本, 进入维护阶段, 地址见分支 <a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Ftree%2Fv1.3">V1.3</a> 。新特性将会在master分支持续更新。</p>&#x000A;<h3>&#x000A;<a id="user-content-77-版本-v141-新特性2016-09-06" class="anchor" href="#77-%E7%89%88%E6%9C%AC-v141-%E6%96%B0%E7%89%B9%E6%80%A72016-09-06"></a>7.7 版本 V1.4.1 新特性[2016-09-06]</h3>&#x000A;<ul>&#x000A;<li>1、项目成功推送maven中央仓库, 中央仓库地址以及依赖如下:&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">&lt;!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ --&gt;</span>&#x000A;<span id="LC2" class="line">&lt;dependency&gt;</span>&#x000A;<span id="LC3" class="line">    &lt;groupId&gt;com.xuxueli&lt;/groupId&gt;</span>&#x000A;<span id="LC4" class="line">    &lt;artifactId&gt;xxl-job-core&lt;/artifactId&gt;</span>&#x000A;<span id="LC5" class="line">    &lt;version&gt;${最新稳定版}&lt;/version&gt;</span>&#x000A;<span id="LC6" class="line">&lt;/dependency&gt;</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;</li>&#x000A;<li>2、为适配中央仓库规则, 项目groupId从com.xxl改为com.xuxueli。</li>&#x000A;<li>3、系统版本不在维护在项目跟pom中,各个子模块单独配置版本配置,解决子模块无法单独编译的问题;</li>&#x000A;<li>4、底层RPC通讯,传输数据的字节长度统计规则优化,可节省50%数据传输量;</li>&#x000A;<li>5、IJobHandler取消任务返回值,原通过返回值判断执行状态,逻辑改为:默认任务执行成功,仅在捕获异常时认定任务执行失败。</li>&#x000A;<li>6、系统公共弹框功能,插件化;</li>&#x000A;<li>7、底层表结构,表明统一大写;</li>&#x000A;<li>8、调度中心,异常处理器JSON响应的ContentType修改,修复浏览器不识别的问题;</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-78-版本-v142-新特性2016-09-29" class="anchor" href="#78-%E7%89%88%E6%9C%AC-v142-%E6%96%B0%E7%89%B9%E6%80%A72016-09-29"></a>7.8 版本 V1.4.2 新特性[2016-09-29]</h3>&#x000A;<ul>&#x000A;<li>1、推送新版本 V1.4.2 至中央仓库, 大版本 V1.4 进入维护阶段;</li>&#x000A;<li>2、任务新增时,任务列表偏移问题修复;</li>&#x000A;<li>3、修复一处因bootstrap不支持模态框重叠而导致的样式错乱的问题, 在任务编辑时会出现该问题;</li>&#x000A;<li>4、调度超时和Handler匹配不到时,调度状态优化;</li>&#x000A;<li>5、因catch异常,导致任务不可终止的问题,给出解决方案, 见文档;</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-79-版本-v150-特性2016-11-13" class="anchor" href="#79-%E7%89%88%E6%9C%AC-v150-%E7%89%B9%E6%80%A72016-11-13"></a>7.9 版本 V1.5.0 特性[2016-11-13]</h3>&#x000A;<ul>&#x000A;<li>1、任务注册: 执行器会周期性自动注册任务, 调度中心将会自动发现注册的任务并触发执行。</li>&#x000A;<li>2、"执行器" 新增参数 "AppName" : 是每个执行器集群的唯一标示AppName, 并周期性以AppName为对象进行自动注册。</li>&#x000A;<li>3、调度中心新增栏目 "执行器管理" : 管理在线的执行器, 通过属性AppName自动发现注册的执行器。只有被管理的执行器才允许被使用;</li>&#x000A;<li>4、"任务组"属性改为"执行器": 每个任务需要绑定指定的执行器, 调度地址通过绑定的执行器获取;</li>&#x000A;<li>5、抛弃"任务机器"属性: 通过任务绑定的执行器, 自动发现注册的远程执行器地址并触发调度请求。</li>&#x000A;<li>6、"公共依赖"中新增DBGlueLoader,基于原生jdbc实现GLUE源码的加载器,减少第三方依赖(mybatis,spring-orm等);精简和优化执行器测配置(针对GLUE任务),降低上手难度;</li>&#x000A;<li>7、表结构调整,底层重构优化;</li>&#x000A;<li>8、"调度中心"自动注册和发现,failover: 调度中心周期性自动注册, 任务回调时可以感知在线的所有调度中心地址, 通过failover的方式进行任务回调,避免回调单点风险。</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-710-版本-v151-特性2016-11-13" class="anchor" href="#710-%E7%89%88%E6%9C%AC-v151-%E7%89%B9%E6%80%A72016-11-13"></a>7.10 版本 V1.5.1 特性[2016-11-13]</h3>&#x000A;<ul>&#x000A;<li>1、底层代码重构和逻辑优化，POM清理以及CleanCode；</li>&#x000A;<li>2、Servlet/JSP Spec设定为3.0/2.2</li>&#x000A;<li>3、Spring升级至3.2.17.RELEASE版本；</li>&#x000A;<li>4、Jetty升级版本至8.2.0.v20160908；</li>&#x000A;<li>5、已推送V1.5.0和V1.5.1至Maven中央仓库；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-711-版本-v152-特性2017-02-28" class="anchor" href="#711-%E7%89%88%E6%9C%AC-v152-%E7%89%B9%E6%80%A72017-02-28"></a>7.11 版本 V1.5.2 特性[2017-02-28]</h3>&#x000A;<ul>&#x000A;<li>1、IP工具类获取IP逻辑优化，IP静态缓存；</li>&#x000A;<li>2、执行器、调度中心，均支持自定义注册IP地址；解决机器多网卡时错误网卡注册的情况；</li>&#x000A;<li>3、任务跨天执行时生成多份日志文件的问题修复；</li>&#x000A;<li>4、底层日志底层日志调整，非敏感日志level调整为debug；</li>&#x000A;<li>5、升级数据库连接池c3p0版本；</li>&#x000A;<li>6、执行器log4j配置优化，去除无效属性；</li>&#x000A;<li>7、底层代码重构和逻辑优化以及CleanCode；</li>&#x000A;<li>8、GLUE依赖注入逻辑优化，支持别名注入；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-712-版本-v160-特性2017-03-13" class="anchor" href="#712-%E7%89%88%E6%9C%AC-v160-%E7%89%B9%E6%80%A72017-03-13"></a>7.12 版本 V1.6.0 特性[2017-03-13]</h3>&#x000A;<ul>&#x000A;<li>1、通讯方案升级，原基于HEX的通讯模型调整为基于HTTP的B-RPC的通讯模型；</li>&#x000A;<li>2、执行器支持手动设置执行地址列表，提供开关切换使用注册地址还是手动设置的地址；</li>&#x000A;<li>3、执行器路由规则：第一个、最后一个、轮询、随机、一致性HASH、最不经常使用、最近最久未使用、故障转移；</li>&#x000A;<li>4、规范线程模型统一，统一线程销毁方案(通过listener或stop方法，容器销毁时销毁线程；Daemon方式有时不太理想)；</li>&#x000A;<li>5、规范系统配置数据，通过配置文件统一管理；</li>&#x000A;<li>6、CleanCode，清理无效的历史参数；</li>&#x000A;<li>7、底层扩展数据结构以及相关表结构调整；</li>&#x000A;<li>8、新建任务默认为非运行状态；</li>&#x000A;<li>9、GLUE模式任务实例更新逻辑优化，原根据超时时间更新改为根据版本号更新，源码变动版本号加一；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-713-版本-v161-特性2017-03-25" class="anchor" href="#713-%E7%89%88%E6%9C%AC-v161-%E7%89%B9%E6%80%A72017-03-25"></a>7.13 版本 V1.6.1 特性[2017-03-25]</h3>&#x000A;<ul>&#x000A;<li>1、Rolling日志；</li>&#x000A;<li>2、WebIDE交互重构；</li>&#x000A;<li>3、通讯增强校验，有效过滤非正常请求；</li>&#x000A;<li>4、权限增强校验，采用动态登录TOKEN（推荐接入内部SSO）；</li>&#x000A;<li>5、数据库配置优化，解决乱码问题；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-714-版本-v162-特性2017-04-25" class="anchor" href="#714-%E7%89%88%E6%9C%AC-v162-%E7%89%B9%E6%80%A72017-04-25"></a>7.14 版本 V1.6.2 特性[2017-04-25]</h3>&#x000A;<ul>&#x000A;<li>1、运行报表：支持实时查看运行数据，如任务数量、调度次数、执行器数量等；以及调度报表，如调度日期分布图，调度成功分布图等；</li>&#x000A;<li>2、JobHandler支持设置任务返回值，在任务逻辑中可以方便的控制任务执行结果；</li>&#x000A;<li>3、资源路径包含空格或中文时资源文件无法加载时，无法准确查看异常信息的问题处理。</li>&#x000A;<li>4、路由策越优化：循环和LFU路由策略计数器自增无上限问题和首次路由压力集中在首台机器的问题修复；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-715-版本-v170-特性2017-05-02" class="anchor" href="#715-%E7%89%88%E6%9C%AC-v170-%E7%89%B9%E6%80%A72017-05-02"></a>7.15 版本 V1.7.0 特性[2017-05-02]</h3>&#x000A;<ul>&#x000A;<li>1、脚本任务：支持以GLUE模式开发和运行脚本任务，包括Shell、Python和Groovy等类型脚本;</li>&#x000A;<li>2、新增spring-boot类型执行器example项目；</li>&#x000A;<li>3、升级jetty版本至9.2；</li>&#x000A;<li>4、任务运行日志移除log4j组件依赖，改为底层自主实现，从而取消了对日志组件的依赖限制；</li>&#x000A;<li>5、执行器移除GlueLoader依赖，改为推送方式实现，从而GLUE源码加载不再依赖JDBC；</li>&#x000A;<li>6、登录拦截Redirect时获取项目名，解决非根据目录发布时跳转404问题；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-716-版本-v171-特性2017-05-08" class="anchor" href="#716-%E7%89%88%E6%9C%AC-v171-%E7%89%B9%E6%80%A72017-05-08"></a>7.16 版本 V1.7.1 特性[2017-05-08]</h3>&#x000A;<ul>&#x000A;<li>1、运行日志读写编码统一为UTF-8，解决windows环境下日志乱码问题；</li>&#x000A;<li>2、通讯超时时间限定为10s，避免异常情况下调度线程占用；</li>&#x000A;<li>3、执行器，server启动、销毁和注册逻辑调整；</li>&#x000A;<li>4、JettyServer关闭逻辑优化，修复执行器无法正常关闭导致端口占用和频繁打印c3p0日志的问题；</li>&#x000A;<li>5、JobHandler中开启子线程时，支持子线程输出执行日志并通过Rolling查看。</li>&#x000A;<li>6、任务日志清理功能；</li>&#x000A;<li>7、弹框组件统一替换为layer；</li>&#x000A;<li>8、升级quartz版本至2.3.0；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-717-版本-v172-特性2017-05-17" class="anchor" href="#717-%E7%89%88%E6%9C%AC-v172-%E7%89%B9%E6%80%A72017-05-17"></a>7.17 版本 V1.7.2 特性[2017-05-17]</h3>&#x000A;<ul>&#x000A;<li>1、阻塞处理策略：调度过于密集执行器来不及处理时的处理策略，策略包括：单机串行（默认）、丢弃后续调度、覆盖之前调度；</li>&#x000A;<li>2、失败处理策略；调度失败时的处理策略，策略包括：失败告警（默认）、失败重试；</li>&#x000A;<li>3、通讯时间戳超时时间调整为180s；</li>&#x000A;<li>4、执行器与数据库彻底解耦，但是执行器需要配置调度中心集群地址。调度中心提供API供执行器回调和心跳注册服务，取消调度中心内部jetty，心跳周期调整为30s，心跳失效为三倍心跳；</li>&#x000A;<li>5、执行参数编辑时丢失问题修复；</li>&#x000A;<li>6、新增任务测试Demo，方便在开发时进行任务逻辑测试；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-718-版本-v180-特性2017-07-17" class="anchor" href="#718-%E7%89%88%E6%9C%AC-v180-%E7%89%B9%E6%80%A72017-07-17"></a>7.18 版本 V1.8.0 特性[2017-07-17]</h3>&#x000A;<ul>&#x000A;<li>1、任务Cron更新逻辑优化，改为rescheduleJob，同时防止cron重复设置；</li>&#x000A;<li>2、API回调服务失败状态码优化，方便问题排查；</li>&#x000A;<li>3、XxlJobLogger的日志多参数支持；</li>&#x000A;<li>4、路由策略新增 "忙碌转移" 模式：按照顺序依次进行空闲检测，第一个空闲检测成功的机器选定为目标执行器并发起调度；</li>&#x000A;<li>5、路由策略代码重构；</li>&#x000A;<li>6、执行器重复注册问题修复；</li>&#x000A;<li>7、任务线程轮空30次后自动销毁，降低低频任务的无效线程消耗。</li>&#x000A;<li>8、执行器任务执行结果批量回调，降低回调频率提升执行器性能；</li>&#x000A;<li>9、springboot版本执行器，取消XML配置，改为类配置方式；</li>&#x000A;<li>10、执行日志，支持根据运行 "状态" 筛选日志；</li>&#x000A;<li>11、调度中心任务注册检测逻辑优化；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-719-版本-v181-特性2017-07-30" class="anchor" href="#719-%E7%89%88%E6%9C%AC-v181-%E7%89%B9%E6%80%A72017-07-30"></a>7.19 版本 V1.8.1 特性[2017-07-30]</h3>&#x000A;<ul>&#x000A;<li>1、分片广播任务：执行器集群部署时，任务路由策略选择"分片广播"情况下，一次任务调度将会广播触发集群中所有执行器执行一次任务，可根据分片参数处理分片任务；</li>&#x000A;<li>2、动态分片：分片广播任务以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。</li>&#x000A;<li>3、执行器JobHandler禁止命名冲突；</li>&#x000A;<li>4、执行器集群地址列表进行自然排序；</li>&#x000A;<li>5、调度中心，DAO层代码精简优化并且新增测试用例覆盖；</li>&#x000A;<li>6、调度中心API服务改为自研RPC形式，统一底层通讯模型；</li>&#x000A;<li>7、新增调度中心API服务测试Demo，方便在调度中心API扩展和测试；</li>&#x000A;<li>8、任务列表页交互优化，更换执行器分组时自动刷新任务列表，新建任务时默认定位在当前执行器位置；</li>&#x000A;<li>9、访问令牌（accessToken）：为提升系统安全性，调度中心和执行器进行安全性校验，双方AccessToken匹配才允许通讯；</li>&#x000A;<li>10、springboot版本执行器，升级至1.5.6.RELEASE版本；</li>&#x000A;<li>11、统一maven依赖版本管理；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-720-版本-v182-特性2017-09-04" class="anchor" href="#720-%E7%89%88%E6%9C%AC-v182-%E7%89%B9%E6%80%A72017-09-04"></a>7.20 版本 V1.8.2 特性[2017-09-04]</h3>&#x000A;<ul>&#x000A;<li>1、项目主页搭建：提供中英文文档：<a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fxxl-job">https://www.xuxueli.com/xxl-job</a>&#x000A;</li>&#x000A;<li>2、JFinal执行器Sample示例项目；</li>&#x000A;<li>3、事件触发：除了"Cron方式"和"任务依赖方式"触发任务执行之外，支持基于事件的触发任务方式。调度中心提供触发任务单次执行的API服务，可根据业务事件灵活触发。</li>&#x000A;<li>4、执行器摘除：执行器销毁时，主动通知调度中心并摘除对应执行器节点，提高执行器状态感知的时效性。</li>&#x000A;<li>5、执行器手动设置IP时将会绑定Host；</li>&#x000A;<li>6、规范项目目录，方便扩展多执行器；</li>&#x000A;<li>7、解决执行器回调URL不支持配置HTTPS时问题；</li>&#x000A;<li>8、执行器回调线程销毁前, 批量回调队列中数据，防止任务结果丢失；</li>&#x000A;<li>9、调度中心任务监控线程销毁时，批量对失败任务告警，防止告警信息丢失；</li>&#x000A;<li>10、任务日志文件路径时间戳格式化时SimpleDateFormat并发问题解决；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-721-版本-v190-特性2017-12-29" class="anchor" href="#721-%E7%89%88%E6%9C%AC-v190-%E7%89%B9%E6%80%A72017-12-29"></a>7.21 版本 V1.9.0 特性[2017-12-29]</h3>&#x000A;<ul>&#x000A;<li>1、新增Nutz执行器Sample示例项目；</li>&#x000A;<li>2、新增任务运行模式 "GLUE模式(NodeJS) "，支持NodeJS脚本任务；</li>&#x000A;<li>3、脚本任务Shell、Python和Nodejs等支持获取分片参数；</li>&#x000A;<li>4、失败重试，完整支持：调度中心调度失败且启用"失败重试"策略时，将会自动重试一次；执行器执行失败且回调失败重试状态（新增失败重试状态返回值）时，也将会自动重试一次；</li>&#x000A;<li>5、失败告警策略扩展：默认提供邮件失败告警，可扩展短信等，扩展代码位置为 "JobFailMonitorHelper.failAlarm"；</li>&#x000A;<li>6、执行器端口支持自动生成(小于等于0时)，避免端口定义冲突；</li>&#x000A;<li>7、调度报表优化，支持时间区间筛选；</li>&#x000A;<li>8、Log组件支持输出异常栈信息，底层实现优化；</li>&#x000A;<li>9、告警邮件样式优化，调整为表格形式，邮件组件调整为commons-email简化邮件操作；</li>&#x000A;<li>10、项目依赖全量升级至较新稳定版本，如spring、jackson等等；</li>&#x000A;<li>11、任务日志，记录发起调度的机器信息；</li>&#x000A;<li>12、交互优化，如登录注销；</li>&#x000A;<li>13、任务Cron长度扩展支持至128位，支持负责类型Cron设置；</li>&#x000A;<li>14、执行器地址录入交互优化，地址长度扩展支持至512位，支持大规模执行器集群配置；</li>&#x000A;<li>15、任务参数“IJobHandler.execute”入参改为“String params”，增强入参通用性。</li>&#x000A;<li>16、IJobHandler提供init/destroy方法，支持在相应任务线程初始化和销毁时进行附加操作；</li>&#x000A;<li>17、任务注解调整为 “@JobHandler”，与任务抽象接口统一；</li>&#x000A;<li>18、修复任务监控线程被耗时任务阻塞的问题；</li>&#x000A;<li>19、修复任务监控线程无法监控任务触发和执行状态均未0的问题；</li>&#x000A;<li>20、执行器动态代理对象，拦截非业务方法的执行；</li>&#x000A;<li>21、修复JobThread捕获Error错误不更新JobLog的问题；</li>&#x000A;<li>22、修复任务列表界面左侧菜单合并时样式错乱问题；</li>&#x000A;<li>23、调度中心项目日志配置改为xml文件格式；</li>&#x000A;<li>24、Log地址格式兼容，支持非"/"结尾路径配置；</li>&#x000A;<li>25、底层系统日志级别规范调整，清理遗留代码；</li>&#x000A;<li>26、建表SQL优化，支持同步创建制定编码的库和表；</li>&#x000A;<li>27、系统安全性优化，登录Token写Cookie时进行MD5加密，同时Cookie启用HttpOnly；</li>&#x000A;<li>28、新增"任务ID"属性，移除"JobKey"属性，前者承担所有功能，方便后续增强任务依赖功能。</li>&#x000A;<li>29、任务循环依赖问题修复，避免子任务与父任务重复导致的调度死循环；</li>&#x000A;<li>30、任务列表新增筛选条件 "任务描述"，快速检索任务；</li>&#x000A;<li>31、执行器Log文件定期清理功能：执行器新增配置项（"xxl.job.executor.logretentiondays"）日志保存天数，日志文件过期自动删除。</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-722-版本-v191-特性2018-02-22" class="anchor" href="#722-%E7%89%88%E6%9C%AC-v191-%E7%89%B9%E6%80%A72018-02-22"></a>7.22 版本 V1.9.1 特性[2018-02-22]</h3>&#x000A;<ul>&#x000A;<li>1、国际化：调度中心实现国际化，支持中文、英文两种语言，默认为中文。</li>&#x000A;<li>2、调度报表新增"运行中"中状态项；</li>&#x000A;<li>3、调度报表优化，报表SQL调优并且新增LocalCache缓存（缓存时间60s），提高大数据量下报表加载速度；</li>&#x000A;<li>4、修复打包部署时资源文件乱码问题；</li>&#x000A;<li>5、修复新版本chrome滚动到顶部失效问题；</li>&#x000A;<li>6、调度中心配置加载优化，取消对配置文件名的强依赖，支持加载磁盘配置；</li>&#x000A;<li>7、修复脚本任务Log文件未正常close的问题；</li>&#x000A;<li>8、项目依赖全量升级至较新稳定版本，如spring、jackson等等；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-723-版本-v192-特性2018-10-05" class="anchor" href="#723-%E7%89%88%E6%9C%AC-v192-%E7%89%B9%E6%80%A72018-10-05"></a>7.23 版本 V1.9.2 特性[2018-10-05]</h3>&#x000A;<ul>&#x000A;<li>1、任务超时控制：新增任务属性 "任务超时时间"，并支持自定义，任务运行超时将会主动中断任务；</li>&#x000A;<li>2、任务失败重试次数：新增任务属性 "失败重试次数"，并支持自定义，当任务失败时将会按照预设的失败重试次数主动进行重试；同时收敛废弃其他失败重试策略，如调度失败、执行失败、状态码失败等；</li>&#x000A;<li>3、新增任务运行模式 "GLUE模式(PHP) "，支持php脚本任务；</li>&#x000A;<li>4、新增任务运行模式 "GLUE模式(PowerShell) "，支持PowerShell脚本任务；</li>&#x000A;<li>5、调度全异步处理：任务触发之后，推送到调度队列，多线程并发处理调度请求，提高任务调度速率的同时，避免因网络问题导致quartz调度线程阻塞的问题；</li>&#x000A;<li>6、执行器任务结果落盘优化：执行器回调失败时将任务结果写磁盘，待重启或网络恢复时重试回调任务结果，防止任务执行结果丢失；</li>&#x000A;<li>7、任务日志查询速度大幅提升：百万级别数据量搜索速度提升1000倍；</li>&#x000A;<li>8、调度中心提供API服务，支持通过API服务对任务进行查询、新增、更新、启停等操作；</li>&#x000A;<li>9、底层自研Log组件参数占位符改为"{}"，并修复打印有参日志时参数不匹配导致报错的问题；</li>&#x000A;<li>10、任务回调结果优化，支持展示在Rolling log中，方便问题排查；</li>&#x000A;<li>11、底层LocalCache组件兼容性优化，支持jdk9、jdk10及以上版本编译部署；</li>&#x000A;<li>12、告警邮件固定使用 UTF-8 编码格式，修复由机器编码导致的邮件乱码问题；</li>&#x000A;<li>13、告警邮件中展示失败告警信息；</li>&#x000A;<li>14、告警邮箱支持SSL配置；</li>&#x000A;<li>15、Window机器下File.separator不兼容问题修复；</li>&#x000A;<li>16、脚本任务异常Log输出优化；</li>&#x000A;<li>17、任务线程停止变量修饰符优化；</li>&#x000A;<li>18、脚本任务Log文件流关闭优化；</li>&#x000A;<li>19、任务报表成功、失败和进行中统计问题修复；</li>&#x000A;<li>20、核心依赖Core内部国际化处理；</li>&#x000A;<li>21、默认Quartz线程数调整为50；</li>&#x000A;<li>22、新增左侧菜单"运行报表"；</li>&#x000A;<li>23、执行器手动设置IP时取消绑定Host的操作，该IP仅供执行器注册使用；修复指定外网IP时无法绑定执行器Host的问题；</li>&#x000A;<li>24、取消父子任务不可重复的限制，支持循环任务触发等特殊场景；</li>&#x000A;<li>25、任务调度备注中标注任务触发类型，如Cron触发、父任务触发、API触发等等，方便排查调度日志；</li>&#x000A;<li>26、底层日志组件SimpleDateFormat线程安全问题修复；</li>&#x000A;<li>27、执行器通讯线程优化，corePoolSize从256降低至32；</li>&#x000A;<li>28、任务日志表状态字段类型优化；</li>&#x000A;<li>29、GLUE脚本文件自动清理功能，及时清理过期脚本文件；</li>&#x000A;<li>30、执行器注册方式切换优化，切换自动注册时主动同步在线机器，避免执行器为空的问题；</li>&#x000A;<li>31、跨平台：除了提供Java、Python、PHP等十来种任务模式之外，新增提供基于HTTP的任务模式；</li>&#x000A;<li>32、底层RPC序列化协议调整为hessian2；</li>&#x000A;<li>33、修复表字段 “t.order”与数据库关键字冲突查询失败的问题，</li>&#x000A;<li>34、任务属性枚举 "任务模式、阻塞策略" 国际化优化；</li>&#x000A;<li>35、分片任务失败重试优化，仅重试当前失败的分片；</li>&#x000A;<li>36、任务触发时支持动态传参，调度中心与API服务均提供提供动态参数功能；</li>&#x000A;<li>37、任务执行日志、调度日志字段类型调整，改为text类型并取消字数限制；</li>&#x000A;<li>38、GLUE任务脚本字段类型调整，改为mediumtext类型，提高GLUE长度上限；</li>&#x000A;<li>39、任务监控线程Log输出优化，运行中任务的监控Log改为debug级别，减少非核心日志量；</li>&#x000A;<li>40、项目依赖全量升级至较新稳定版本，如spring、Jackson、groovy等等；</li>&#x000A;<li>41、docker支持：调度中心提供 Dockerfile 方便快速构建docker镜像；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-724-版本-v200-release-notes2018-11-04" class="anchor" href="#724-%E7%89%88%E6%9C%AC-v200-release-notes2018-11-04"></a>7.24 版本 V2.0.0 Release Notes[2018-11-04]</h3>&#x000A;<ul>&#x000A;<li>1、调度中心迁移到 springboot；</li>&#x000A;<li>2、底层通讯组件迁移至 xxl-rpc；</li>&#x000A;<li>3、容器化：提供官方docker镜像，并实时更新推送dockerhub（docker pull xuxueli/xxl-job-admin），进一步实现产品开箱即用；</li>&#x000A;<li>4、新增无框架执行器Sample示例项目 "xxl-job-executor-sample-frameless"。不依赖第三方框架，只需main方法即可启动运行执行器；</li>&#x000A;<li>5、命令行任务：原生提供通用命令行任务Handler（Bean任务，"CommandJobHandler"）；业务方只需要提供命令行即可；</li>&#x000A;<li>6、任务状态优化，仅运行状态"NORMAL"任务关联至quartz，降低quartz底层数据存储与调度压力；</li>&#x000A;<li>7、任务状态规范：新增任务默认停止状态，任务更新时保持任务状态不变；</li>&#x000A;<li>8、IP获取逻辑优化，优先遍历网卡来获取可用IP；</li>&#x000A;<li>9、任务新增的API服务接口返回任务ID，方便调用方实用；</li>&#x000A;<li>10、组件化优化，移除对 spring 的依赖：非spring应用选用 "XxlJobExecutor" 、spring应用选用 "XxlJobSpringExecutor" 作为执行器组件；</li>&#x000A;<li>11、任务RollingLog展示逻辑优化，修复超时任务无法查看的问题；</li>&#x000A;<li>12、多项UI组件升级到最新版本，如：CodeMirror、Echarts、Jquery 等；</li>&#x000A;<li>13、项目依赖升级 groovy 至较新稳定版本；pom清理；</li>&#x000A;<li>14、子任务失败重试重试逻辑优化，子任务失败时将会按照其预设的失败重试次数主动进行重试</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-725-版本-v201-release-notes2018-11-09" class="anchor" href="#725-%E7%89%88%E6%9C%AC-v201-release-notes2018-11-09"></a>7.25 版本 v2.0.1 Release Notes[2018-11-09]</h3>&#x000A;<ul>&#x000A;<li>1、左侧菜单折叠动画问题修复；</li>&#x000A;<li>2、调度报表日期分布图默认值统一；</li>&#x000A;<li>3、freemarker对数字默认加千分位问题修复，解决日志ID被分隔导致查看日志失败问题；</li>&#x000A;<li>4、底层通讯组件升级，修复通讯异常时无效等待的问题；</li>&#x000A;<li>5、执行器启动之后jetty停止的问题修复；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-726-版本-v202-release-notes2019-04-20" class="anchor" href="#726-%E7%89%88%E6%9C%AC-v202-release-notes2019-04-20"></a>7.26 版本 v2.0.2 Release Notes[2019-04-20]</h3>&#x000A;<ul>&#x000A;<li>1、底层通讯方案优化：升级较新版本xxl-rpc，由"JETTY"方案调整为"NETTY_HTTP"方案，执行器内嵌netty-http-server提供服务，调度中心复用容器端口提供服务；</li>&#x000A;<li>2、任务告警逻辑调整，改为通过扫描失败日志方式触发。一方面精确扫描失败任务，降低扫描范围；另一方面取消内存队列，降低线程内存消耗；</li>&#x000A;<li>3、Quartz触发线程池废弃并替换为 "XxlJobThreadPool"，降低线程切换、内存占用带来的消耗，提高调度性能；</li>&#x000A;<li>4、调度线程池隔离，拆分为"Fast"和"Slow"两个线程池，1分钟窗口期内任务耗时达500ms超过10次，该窗口期内判定为慢任务，慢任务自动降级进入"Slow"线程池，避免耗尽调度线程，提高系统稳定性；</li>&#x000A;<li>5、执行器热部署时JobHandler重新初始化，修复由此导致的 "jobhandler naming conflicts." 问题；</li>&#x000A;<li>6、新增Class的加载缓存，解决频繁加载Class会使jvm的方法区空间不足导致OOM的问题；</li>&#x000A;<li>7、任务支持更换绑定执行器，方便任务分组转移和管理；</li>&#x000A;<li>8、调度中心告警邮件发送组件改为 “spring-boot-starter-mail”；</li>&#x000A;<li>9、记住密码功能优化，选中时永久记住；非选中时关闭浏览器即登出；</li>&#x000A;<li>10、项目依赖升级至较新稳定版本，如quartz、spring、jackson、groovy、xxl-rpc等等；</li>&#x000A;<li>11、精简项目，取消第三方依赖，如 commons-collections4、commons-lang3 ;</li>&#x000A;<li>12、执行器回调日志落盘方案复用RPC序列化方案，并移除Jackson依赖；</li>&#x000A;<li>13、底层Log调优，应用正常终止取消异常栈信息打印；</li>&#x000A;<li>14、交互优化，尽量避免新开页面窗口；仅WebIDE支持新开页，并提供窗口快速关闭按钮；任务启、停、删除、触发等轻操作提示改为toast方式，</li>&#x000A;<li>15、任务暂停、删除优化，避免quartz delete不完整导致任务脏数据；</li>&#x000A;<li>16、任务回调、心跳注册成功日志优化，非核心常规日志调整为debug级别，降低冗余日志输出；</li>&#x000A;<li>17、调整首页报表默认区间为本周，避免日志量太大查询缓慢；</li>&#x000A;<li>18、LRU路由更新不及时问题修复；</li>&#x000A;<li>19、任务失败告警邮件发送逻辑优化；</li>&#x000A;<li>20、调度日志排序逻辑调整为按照调度时间倒序，兼容TIDB等主键不连续日志存储组件；</li>&#x000A;<li>21、执行器优雅停机优化；</li>&#x000A;<li>22、连接池配置优化，增强连接有效性验证；</li>&#x000A;<li>23、JobHandler#msg长度限制，修复异常情况下日志超长导致内存溢出的问题；</li>&#x000A;<li>24、升级xxl-rpc至较新版本，修复springboot 2.x版本兼容性问题；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-727-版本-v210-release-notes2019-07-07" class="anchor" href="#727-%E7%89%88%E6%9C%AC-v210-release-notes2019-07-07"></a>7.27 版本 v2.1.0 Release Notes[2019-07-07]</h3>&#x000A;<ul>&#x000A;<li>1、自研调度组件，移除quartz依赖：一方面是为了精简系统降低冗余依赖，另一方面是为了提供系统的可控度与稳定性；&#x000A;<ul>&#x000A;<li>触发：单节点周期性触发，运行事件如delayqueue；</li>&#x000A;<li>调度：集群竞争，负载方式协同处理，锁竞争-更新触发信息-推送时间轮-锁释放-锁竞争；</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>2、底层表结构重构：移除11张quartz相关表，并对现有表结构优化梳理；</li>&#x000A;<li>3、任务日志主键调整为long数据类型，防止海量日志情况下数据溢出；</li>&#x000A;<li>4、底层线程模型重构：移除Quartz线程池，降低系统线程与内存开销；</li>&#x000A;<li>5、用户管理：支持在线管理系统用户，存在管理员、普通用户两种角色；</li>&#x000A;<li>6、权限管理：执行器维度进行权限控制，管理员拥有全量权限，普通用户需要分配执行器权限后才允许相关操作；</li>&#x000A;<li>7、调度线程池参数调优；</li>&#x000A;<li>8、注册表索引优化，缓解锁表问题；</li>&#x000A;<li>9、新增Jboot执行器Sample示例项目；</li>&#x000A;<li>10、任务列表优化，支持根据 "任务状态"、"负责人" 属性筛选任务；</li>&#x000A;<li>11、任务日志列表交互优化，操作按钮合并为分割按钮；</li>&#x000A;<li>12、项目依赖升级至较新稳定版本，如spring、springboot、groovy、xxl-rpc等等；并清理冗余POM；</li>&#x000A;<li>13、升级xxl-rpc至较新版本，修复代理服务初始化时远程服务不可用导致长连冗余创建的问题;</li>&#x000A;<li>14、首页调度报表的日期排序在TIDB下乱序问题修复；</li>&#x000A;<li>15、调度中心与执行器双向通讯超时时间调整为3s；</li>&#x000A;<li>16、调度组件销毁流程优化，先停止调度线程，然后等待时间轮内存量任务处理完成，最终销毁时间轮线程；</li>&#x000A;<li>17、执行器回调线程优化，回调地址为空时销毁问题修复；</li>&#x000A;<li>18、HttpJobHandler优化，响应数据指定UTF-8格式，避免中文乱码；</li>&#x000A;<li>19、代码优化，ConcurrentHashMap变量类型改为ConcurrentMap，避免因不同版本实现不同导致的兼容性问题；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-728-版本-v211-release-notes2019-11-24" class="anchor" href="#728-%E7%89%88%E6%9C%AC-v211-release-notes2019-11-24"></a>7.28 版本 v2.1.1 Release Notes[2019-11-24]</h3>&#x000A;<ul>&#x000A;<li>1、 调度中心日志自动清理功能（至此，调度中心/执行器均支持日志自动清理，过期天数均默认设置为30天）：调度中心新增配置项（"xxl.job.logretentiondays"）日志保存天数，过期日志自动清理；解决海量日志情况下日志表慢SQL问题；限制大于等于7时生效，否则关闭清理功能，默认为30；</li>&#x000A;<li>2、 调度报表优化：新增日志报表的存储表，三天内的任务日志会以每分钟一次的频率异步同步至报表中；任务报表仅读取报表数据，极大提升加载速度；</li>&#x000A;<li>3、 Cron在线生成工具：任务新增、编辑框通过组件在线生成Cron表达式；</li>&#x000A;<li>4、 Cron下次执行时间查询：支持通过界面在线查看后续连续5次执行时间；</li>&#x000A;<li>5、 调度中心新增应用健康检查功能，借助“spring-boot-starter-actuator”，相对地址 “/actuator/health”；</li>&#x000A;<li>6、 DB脚本默认编码改为utf8mb4，修复字符乱码问题(建议Mysql版本5.7+)；</li>&#x000A;<li>7、 调度中心任务平均分配，触发组件每次获取与线程池数量相关数量的任务，避免大量任务集中在单个调度中心集群节点；</li>&#x000A;<li>8、 任务触发组件优化，预加载频率正常1s一次，当预加载轮空时主动休眠一个加载周期，动态降低加载频率从而降低DB压力；</li>&#x000A;<li>9、 调度组件优化：针对永远不会触发的Cron禁止配置和启动；任务Cron最后一次触发后再也不会触发时，比如一次性任务，主动停止相关任务；</li>&#x000A;<li>10、DB重连优化，修复DB宕机重连后任务调度停止的问题，重连后自动加入调度集群触发任务调度；</li>&#x000A;<li>11、注册监控线程优化，降低死锁几率；</li>&#x000A;<li>12、调度中心日志删除优化，改为分页获取ID并根据ID删除的方式，避免批量删除海量日志导致死锁问题；</li>&#x000A;<li>13、任务重试时参数丢失的问题修复；</li>&#x000A;<li>14、调度中心移除SQL中的 "now()" 函数；集群部署时不再依赖DB时钟，仅需要保证调度中心应用节点时钟一致即可；</li>&#x000A;<li>15、任务触发组件加载顺序调整，避免小概率情况下组件随机加载顺序导致的I18N的NPE问题;</li>&#x000A;<li>16、JobThread自销毁优化，避免并发触发导致triggerQueue中任务丢失问题；</li>&#x000A;<li>17、调度中心密码限制18位，修复修改密码超过18位无法登录的问题；</li>&#x000A;<li>18、任务告警组件分页参数无效问题修复；</li>&#x000A;<li>19、升级xxl-rpc版本：服务端线程优化，降低线程内存开销；IpUtil优化：增加连通性校，过滤明确非法的网卡；</li>&#x000A;<li>20、调度中心回调API服务改为restful方式；</li>&#x000A;<li>21、UI优化，任务列表和日志列表数据表格宽度比例调整，避免数据换行提升体验；</li>&#x000A;<li>22、登录界面取消默认填写的登录账号密码；</li>&#x000A;<li>23、执行器表属性调整，"顺序" 属性调整为整型，解决执行器数据较多时无法正确排序的问题；</li>&#x000A;<li>24、任务列表交互优化，支持查看任务所属执行器的注册节点；</li>&#x000A;<li>25、项目依赖升级至较新稳定版本，如spring、spring-boot、mybatis、slf4j、groovy等等；</li>&#x000A;<li>26、日志组件优化：调度中心支持控制每次请求最大加载行数，日志量太大时分批请求，避免单次加载日志量太大阻塞页面；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-729-版本-v212-release-notes2019-12-12" class="anchor" href="#729-%E7%89%88%E6%9C%AC-v212-release-notes2019-12-12"></a>7.29 版本 v2.1.2 Release Notes[2019-12-12]</h3>&#x000A;<ul>&#x000A;<li>1、方法任务支持：由原来基于JobHandler类任务开发方式，优化为支持基于方法的任务开发方式；因此，可以支持单个类中开发多个任务方法，进行类复用</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">@XxlJob("demoJobHandler")</span>&#x000A;<span id="LC2" class="line">public ReturnT&lt;String&gt; execute(String param) {</span>&#x000A;<span id="LC3" class="line">    XxlJobLogger.log("hello world");</span>&#x000A;<span id="LC4" class="line">    return ReturnT.SUCCESS;</span>&#x000A;<span id="LC5" class="line">}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<ul>&#x000A;<li>2、移除commons-exec，采用原生方式实现，降低第三方依赖；</li>&#x000A;<li>3、执行器回调乱码问题修复；</li>&#x000A;<li>4、调度中心dispatcher servlet加载顺序优化；</li>&#x000A;<li>5、执行器回调地址https兼容支持；</li>&#x000A;<li>6、多个项目依赖升级至较新稳定版本；</li>&#x000A;<li>注意：最新版本 "XxlJobSpringExecutor" 逻辑有调整，历史项目中该组件的配置方式请参考Sample示例项目进行调整，尤其注意需要移除组件的init和destroy方法；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-730-版本-v220-release-notes2020-04-14" class="anchor" href="#730-%E7%89%88%E6%9C%AC-v220-release-notes2020-04-14"></a>7.30 版本 v2.2.0 Release Notes[2020-04-14]</h3>&#x000A;<ul>&#x000A;<li>1、RESTful API：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。</li>&#x000A;<li>2、任务复制功能：点击复制是弹出新建任务弹框，并初始化被复制任务信息；</li>&#x000A;<li>3、任务手动执行一次的时候，支持指定本次执行的机器地址，为空则从执行器获取；</li>&#x000A;<li>4、任务结果丢失处理：调度记录停留在 "运行中" 状态超过10min，且对应执行器心跳注册失败不在线，则将本地调度主动标记失败；</li>&#x000A;<li>5、调度中心升级springboot2.x；因此，系统要求JDK8+；</li>&#x000A;<li>6、XxlJob注解扫描方式优化，支持查找父类以及接口和基于类代理等常见情况；修复任务为空时小概率NPE问题；</li>&#x000A;<li>7、移除旧类注解JobHandler，推荐使用基于方法注解 "@XxlJob" 的方式进行任务开发；(如需保留类注解JobHandler使用方式，可以参考旧版逻辑定制开发);</li>&#x000A;<li>8、任务告警组件模块化：如果需要新增一种告警方式，只需要新增一个实现 "com.xxl.job.admin.core.alarm.JobAlarm" 接口的告警实现即可，更加灵活、方便定制；</li>&#x000A;<li>9、调度中心国际化完善：新增 "中文繁体" 支持。默认为 "zh_CN"/中文简体, 可选范围为 "zh_CN"/中文简体, "zh_TC"/中文繁体 and "en"/英文；</li>&#x000A;<li>10、执行器注册逻辑优化：新增配置项 ”注册地址 / xxl.job.executor.address“，优先使用该配置作为注册地址，为空时使用内嵌服务 ”IP:PORT“ 作为注册地址。从而更灵活的支持容器类型执行器动态IP和动态映射端口问题。</li>&#x000A;<li>11、默认数据库连接池调整为hikari，移除tomcat-jdbc依赖；</li>&#x000A;<li>12、多个项目依赖升级至较新稳定版本，如mybatis、groovy和mysql驱动等；</li>&#x000A;<li>13、执行器优雅停机优化，修复任务线程中断未join导致回调丢失的问题；</li>&#x000A;<li>14、一致性哈希路由策略优化：默认虚拟节点数量调整为100，提高路由的均衡性；</li>&#x000A;<li>15、通用HTTP任务Handler（httpJobHandler）优化，扩展自定义参数信息，示例参数如下；</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">url: http://www.xxx.com</span>&#x000A;<span id="LC2" class="line">method: get 或 post</span>&#x000A;<span id="LC3" class="line">data: post-data</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<ul>&#x000A;<li>16、SQL脚本编码默认utf8mb4执行，避免小概率下容器环境中乱码问题；</li>&#x000A;<li>17、Web IDE交互问题修复：输入源码备注之后按回车跳转error问题处理；</li>&#x000A;<li>18、执行器初始化逻辑优化：修复懒加载的Bean被提前初始化问题；</li>&#x000A;<li>19、执行器注册默认值优化；</li>&#x000A;<li>20、修复bootstrap.min.css.map 404问题；</li>&#x000A;<li>21、执行器UI交互优化,移除冗余order属性；</li>&#x000A;<li>22、执行备注消息长度限制，修复数据超长无法存储导致导致回调失败的问题；&#x000A;注意：XxlJobSpringExecutor组件个别字段调整：“appName” 调整为 “appname” ，升级时该组件时需要注意；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-731-版本-v230-release-notes2021-02-09" class="anchor" href="#731-%E7%89%88%E6%9C%AC-v230-release-notes2021-02-09"></a>7.31 版本 v2.3.0 Release Notes[2021-02-09]</h3>&#x000A;<ul>&#x000A;<li>1、【新增】调度过期策略：调度中心错过调度时间的补偿处理策略，包括：忽略、立即补偿触发一次等；</li>&#x000A;<li>2、【新增】触发策略：除了常规Cron、API、父子任务触发方式外，新增提供 "固定间隔触发、（固定延时触发，实验中）" 新触发方式；</li>&#x000A;<li>3、【新增】新增任务辅助工具 "XxlJobHelper"：提供统一任务辅助能力，包括：任务上下文信息维护获取（任务参数、任务ID、分片参数）、日志输出、任务结果设置……等；&#x000A;<ul>&#x000A;<li>3.1、"ShardingUtil" 组件废弃：改用 "XxlJobHelper.getShardIndex()/getShardTotal();" 获取分片参数；</li>&#x000A;<li>3.2、"XxlJobLogger" 组件废弃：改用 "XxlJobHelper.log" 进行日志输出；</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>4、【优化】任务核心类 "IJobHandler" 的 "execute" 方法取消出入参设计。改为通过 "XxlJobHelper.getJobParam" 获取任务参数并替代方法入参，通过 "XxlJobHelper.handleSuccess/handleFail" 设置任务结果并替代方法出参，示例代码如下；</li>&#x000A;</ul>&#x000A;<div class="white"><div class="highlight markdown-code-block">&#x000A;<pre><span id="LC1" class="line">@XxlJob("demoJobHandler")</span>&#x000A;<span id="LC2" class="line">public void execute() {</span>&#x000A;<span id="LC3" class="line">  String param = XxlJobHelper.getJobParam();    // 获取参数</span>&#x000A;<span id="LC4" class="line">  XxlJobHelper.handleSuccess();                 // 设置任务结果</span>&#x000A;<span id="LC5" class="line">}</span></pre>&#x000A;<div class="markdown-code-block-copy-btn"></div>&#x000A;</div></div>&#x000A;<ul>&#x000A;<li>5、【优化】Cron编辑器增强：Cron编辑器修改cron时可实时查看最近运行时间;</li>&#x000A;<li>6、【优化】执行器示例项目规范整理；</li>&#x000A;<li>7、【优化】任务调度生命周期重构：调度（schedule）、触发(trigger)、执行（handle）、回调(callback)、结束（complete）；</li>&#x000A;<li>8、【优化】执行器注册组件优化：注册逻辑调整为异步方式，提高注册性能；</li>&#x000A;<li>9、【优化】执行器鉴权校验：执行器启动时主动校验accessToken，为空则主动Warn告警；（已规划安全强化：AccessToken动态生成、动态启停等）</li>&#x000A;<li>10、【优化】邮箱告警配置优化：将"spring.mail.from"与"spring.mail.username"属性拆分开，更加灵活的支持一些无密码邮箱服务；</li>&#x000A;<li>11、【优化】多个项目依赖升级至较新稳定版本，如netty、groovy、spring、springboot、mybatis等；</li>&#x000A;<li>12、【优化】UI组件常规升级，提升组件稳定性；</li>&#x000A;<li>13、【优化】调度中心页面交互优化：用户管理模块密码列取消；多处表达autocomplete取消；执行器管理模块XSS拦截校验等；</li>&#x000A;<li>14、【优化】调度中心任务状态探测慢SQL问题优化；</li>&#x000A;<li>15、【修复】GLUE-Java模式任务，init/destroy无法执行问题修复；</li>&#x000A;<li>16、【修复】Cron编辑器问题修复：修复小概率情况下cron单个字段修改时导致其他字段被重置问题；</li>&#x000A;<li>17、【修复】通用HTTP任务Handler（httpJobHandler）优化：修复 "setDoOutput(true)" 导致任务请求GetMethod失效问题；</li>&#x000A;<li>18、【修复】执行器Commandhandler示例任务优化，修复极端情况下脚本进程挂起问题；</li>&#x000A;<li>19、【修复】调度通讯组件优化，修复RestFul方式调用 DotNet 版本执行器时心跳检测失败问题；</li>&#x000A;<li>20、【修复】调度中心远程执行日志查询乱码问题修复；</li>&#x000A;<li>21、【修复】调度中心组件加载顺序优化，修复极端情况下调度组件初始慢导致的调度失败问题；</li>&#x000A;<li>22、【修复】执行器注册线程优化，修复极端情况下初始化失败时导致NPE问题；</li>&#x000A;<li>23、【修复】调度线程连接池优化，修复连接有效性校验超时问题；</li>&#x000A;<li>24、【修复】执行器注册表字段优化，解决执行器注册节点过多导致注册信息存储和更新失败的问题；</li>&#x000A;<li>25、【修复】轮训路由策略优化，修复小概率下并发问题；</li>&#x000A;<li>26、【修复】页面redirect跳转后https变为http问题修复；</li>&#x000A;<li>27、【修复】执行器日志清理优化，修复小概率下日志文件为空导致清理异常问题；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-732-版本-v231-release-notes2022-05-21" class="anchor" href="#732-%E7%89%88%E6%9C%AC-v231-release-notes2022-05-21"></a>7.32 版本 v2.3.1 Release Notes[2022-05-21]</h3>&#x000A;<ul>&#x000A;<li>1、【修复】修复风险漏洞，升级问题低版本项目依赖：CVE-2021-2471、CVE-2022-22965等。</li>&#x000A;<li>2、【修复】修复故障告警逻辑，邮箱校验逻辑下放至EmailJobAlarm中，避免对其他告警方式的干扰。</li>&#x000A;<li>3、【优化】调度通讯默认启用accessToken，提升系统安全性（建议生产环境自定义accessToken）。</li>&#x000A;<li>4、【优化】合并多项PR，项目代码结构、健壮性优化：PR-2833、PR-2812、PR-2541、PR-2537、PR-2514、PR-2509、PR-2591。</li>&#x000A;<li>5、【优化】任务线程名优化，提升可读性与问题定位效率(ISSUE-2527)。</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-733-版本-v240-release-notes规划中" class="anchor" href="#733-%E7%89%88%E6%9C%AC-v240-release-notes%E8%A7%84%E5%88%92%E4%B8%AD"></a>7.33 版本 v2.4.0 Release Notes[规划中]</h3>&#x000A;<ul>&#x000A;<li>1、【优化】[规划中]任务日志重构：一次调度只记录一条主任务，维护起止时间和状态。&#x000A;<ul>&#x000A;<li>普通任务：只记录一条主任务；</li>&#x000A;<li>广播任务：记录一条主任务，每个分片任务记录一条次任务，关联在主任务上；</li>&#x000A;<li>重试任务：失败时，新增主任务。所有调度记录，包括入口调度和重试调度，均挂载主任务上。</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>2、【优化】[规划中]分片任务：全部完成后才会出发后置节点；</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-734-版本-v241-release-notes规划中" class="anchor" href="#734-%E7%89%88%E6%9C%AC-v241-release-notes%E8%A7%84%E5%88%92%E4%B8%AD"></a>7.34 版本 v2.4.1 Release Notes[规划中]</h3>&#x000A;<ul>&#x000A;<li>1、[规划中]DAG流程任务&#x000A;<ul>&#x000A;<li>DAG任务：支持参数传递，共享数据：DAG任务创建、管理，DAG任务日志查看、操作；</li>&#x000A;<li>子任务：废弃</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>2、[规划中]多数据库支持，DAO层通过JPA实现，不限制数据库类型；</li>&#x000A;<li>3、[规划中]告警增强：邮件告警 + webhook告警；</li>&#x000A;<li>4、[规划中]安全强化：AccessToken动态生成、动态启停；控制调度、回调；</li>&#x000A;<li>5、[规划中]任务导入导出工具，灵活支持版本升级、迁移等场景。</li>&#x000A;</ul>&#x000A;<h3>&#x000A;<a id="user-content-todo-list" class="anchor" href="#todo-list"></a>TODO LIST</h3>&#x000A;<ul>&#x000A;<li>1、任务分片路由：分片采用一致性Hash算法计算出尽量稳定的分片顺序，即使注册机器存在波动也不会引起分批分片顺序大的波动；目前采用IP自然排序，可以满足需求，待定；</li>&#x000A;<li>2、调度隔离：调度中心针对不同执行器，各自维护不同的调度和远程触发组件。</li>&#x000A;<li>3、调度任务优先级；</li>&#x000A;<li>4、多数据库支持，DAO层通过JPA实现，不限制数据库类型；</li>&#x000A;<li>5、执行器Log清理功能：调度中心Log删除时同步删除执行器中的Log文件；</li>&#x000A;<li>6、延时任务：API触发，支持"动态传参、延时消费"；该功能与 XXL-MQ 冲突，该场景建议用后者；</li>&#x000A;<li>7、调度线程池改为协程方式实现，大幅降低系统内存消耗；</li>&#x000A;<li>8、任务、执行器数据全量本地缓存；新增消息表广播通知；</li>&#x000A;<li>9、忙碌转移优化，全部机器忙碌时不再直接失败；</li>&#x000A;<li>10、任务触发参数优化：支持选择 "Cron触发"、"固定间隔时间触发"、"指定时间点触发"、"不选择" 等；</li>&#x000A;<li>11、调度日志列表加上执行时长列，并支持排序；</li>&#x000A;<li>12、DAG流程任务：&#x000A;<ul>&#x000A;<li>替换子任务，支持参数传递，共享数据：</li>&#x000A;<li>配置并列的"a-b、b-c"路径列表，构成串行、并行、dag任务流程，"dagre-d3"绘图；任务依赖，流程图，子任务+会签任务，各节点日志；支持根据成功、失败选择分支；</li>&#x000A;<li>分片任务：全部完成后才会出发后置节点；</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>13、日期过滤：支持多个时间段排除；</li>&#x000A;<li>14、告警增强：&#x000A;<ul>&#x000A;<li>邮件告警：支持自定义标题、模板格式；</li>&#x000A;<li>webhook告警：支持自定义告警URL、请求体格式；</li>&#x000A;</ul>&#x000A;</li>&#x000A;<li>15、新增任务运行模式 "GLUE模式(GO) "，支持GO任务；</li>&#x000A;<li>16、GLUE 模式 Web Ide 版本对比功能；</li>&#x000A;<li>17、注册中心优化，实时性注册发现：心跳注册间隔10s，refresh失败则首次注册并立即更新注册信息，心跳类似；30s过期销毁；</li>&#x000A;<li>18、提供执行器Docker镜像；</li>&#x000A;<li>19、脚本任务，支持数据参数，新版本仅支持单参数不支持需要兼容；</li>&#x000A;<li>20、批量调度：调度请求入queue，调度线程批量获取调度请求并发起远程调度；提高线程效率；</li>&#x000A;<li>21、执行器端口复用，复用容器端口提供通讯服务；</li>&#x000A;<li>22、分片任务全部成功后触发子任务；</li>&#x000A;<li>23、新增执行器描述属性；任务名称属性；</li>&#x000A;<li>24、自定义失败重试时间间隔；</li>&#x000A;<li>25、任务标签：方便搜索；</li>&#x000A;<li>26、执行器：dag执行器，不需要注册机器；</li>&#x000A;</ul>&#x000A;<h2>&#x000A;<a id="user-content-八其他" class="anchor" href="#%E5%85%AB%E5%85%B6%E4%BB%96"></a>八、其他</h2>&#x000A;<h3>&#x000A;<a id="user-content-81-项目贡献" class="anchor" href="#81-%E9%A1%B9%E7%9B%AE%E8%B4%A1%E7%8C%AE"></a>8.1 项目贡献</h3>&#x000A;<p>欢迎参与项目贡献！比如提交PR修复一个bug，或者新建 <a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Fissues%2F">Issue</a> 讨论新特性或者变更。</p>&#x000A;<h3>&#x000A;<a id="user-content-82-用户接入登记" class="anchor" href="#82-%E7%94%A8%E6%88%B7%E6%8E%A5%E5%85%A5%E7%99%BB%E8%AE%B0"></a>8.2 用户接入登记</h3>&#x000A;<p>更多接入的公司，欢迎在 <a href="https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Fxuxueli%2Fxxl-job%2Fissues%2F1">登记地址</a> 登记，登记仅仅为了产品推广。</p>&#x000A;<h3>&#x000A;<a id="user-content-83-开源协议和版权" class="anchor" href="#83-%E5%BC%80%E6%BA%90%E5%8D%8F%E8%AE%AE%E5%92%8C%E7%89%88%E6%9D%83"></a>8.3 开源协议和版权</h3>&#x000A;<p>产品开源免费，并且将持续提供免费的社区技术支持。个人或企业内部可自由的接入和使用。如有需要可邮件联系作者免费获取项目授权。</p>&#x000A;<ul>&#x000A;<li>Licensed under the GNU General Public License (GPL) v3.</li>&#x000A;<li>Copyright (c) 2015-present, xuxueli.</li>&#x000A;</ul>&#x000A;<hr>&#x000A;<h3>&#x000A;<a id="user-content-捐赠" class="anchor" href="#%E6%8D%90%E8%B5%A0"></a>捐赠</h3>&#x000A;<p>无论捐赠金额多少都足够表达您这份心意，非常感谢 ：）      <a href="https://gitee.com/link?target=https%3A%2F%2Fwww.xuxueli.com%2Fpage%2Fdonate.html">前往捐赠</a></p></div>
<div class='file_line'></div>
<script>
  window.Gitee.initReadmeCatalog();
  toMathMlCode('','markdown-body');
  $('.file_content a, .catalog-li a.anchor').click(function () {
    var anchor = $(this).attr('href')
    window.location.hash = anchor
  })
</script>

</div>
</div>
<div class='tree_progress'></div>
<div class='ui small modal' id='modal-linejump'>
<div class='ui custom form content'>
<div class='field'>
<div class='ui right action input'>
<input placeholder='跳转至某一行...' type='number'>
<div class='ui orange button'>
跳转
</div>
</div>
</div>
</div>
</div>

<div class='complaint'>
<div class='ui modal small form' id='landing-comments-complaint-modal'>
<i class='iconfont icon-close close'></i>
<div class='header'>
举报
</div>
<div class='content'>
<div class='appeal-success-tip hide'>
<i class='iconfont icon-ic_msg_success'></i>
<div class='appeal-success-text'>
举报成功
</div>
<span>
我们将于2个工作日内通过站内信反馈结果给你！
</span>
</div>
<div class='appeal-tip'>
请认真填写举报原因，尽可能描述详细。
</div>
<div class='ui form appeal-form'>
<div class='inline field'>
<label class='left-part appeal-type-wrap'>
举报类型
</label>
<div class='ui dropdown selection' id='appeal-comments-types'>
<div class='text default'>
请选择举报类型
</div>
<i class='dropdown icon'></i>
<div class='menu'></div>
</div>
</div>
<div class='inline field'>
<label class='left-part'>
举报原因
</label>
<textarea class='appeal-reason' id='appeal-comment-reason' name='msg' placeholder='请说明举报原因' rows='3'></textarea>
</div>
<div class='ui message callback-msg hide'></div>
<div class='ui small error text message exceeded-size-tip'></div>
</div>
</div>
<div class='actions'>
<div class='ui button blank cancel'>
取消
</div>
<div class='ui orange icon button disabled ok' id='complaint-comment-confirm'>
发送
</div>
</div>
</div>
<script>
  var $complaintCommentsModal = $('#landing-comments-complaint-modal'),
      $complainCommentType = $complaintCommentsModal.find('#appeal-comments-types'),
      $complaintModalTip = $complaintCommentsModal.find('.callback-msg'),
      $complaintCommentsContent = $complaintCommentsModal.find('.appeal-reason'),
      $complaintCommentBtn = $complaintCommentsModal.find('#complaint-comment-confirm'),
      complaintSending = false,
      initedCommentsType = false;
  
  function initCommentsTypeList() {
    if (!initedCommentsType) {
      $.ajax({
        url: "/appeals/fetch_types",
        method: 'get',
        data: {'type': 'comment'},
        success: function (data) {
          var result = '';
          for (var i = 0; i < data.length; i++) {
            result = result + "<div class='item' data-value='" + data[i].id + "'>" + data[i].name + "</div>";
          }
          $complainCommentType.find('.menu').html(result);
        }
      });
      $complainCommentType.dropdown({showOnFocus: false});
      initedCommentsType = true;
    }
  }
  $complainCommentType.on('click', function() {
    $complaintCommentsModal.modal({
      autofocus: false,
      onApprove: function() {
        return false;
      },
      onHidden: function() {
        restoreCommonentDefault();
      }
    }).modal('show');
  });
  
  $complaintCommentsContent.on('change keyup', function(e) {
    var content = $(this).val();
    if ($.trim(content).length > 0 && $complainCommentType.dropdown('get value').length > 0 ) {
      $complaintCommentBtn.removeClass('disabled');
      return;
    }
    $complaintCommentBtn.addClass('disabled');
  });
  
  
  $complainCommentType.dropdown({
    showOnFocus: false,
    onChange: function(value, text, $selectedItem) {
      if (value.length > 0 && $.trim($complaintCommentsContent.val()).length > 0) {
        $complaintCommentBtn.removeClass('disabled');
        return
      }
      $complaintCommentBtn.addClass('disabled');
    }
  });
  
  function restoreCommonentDefault() {
    $complainCommentType.dropdown('restore defaults');
    $complaintCommentsContent.val('');
    $('.exceeded-size-tip').text('').hide();
    $complaintModalTip.text('').hide();
    setTimeout(function() {
      setCommentSendTip(false);
    }, 1500);
  }
  
  $complaintCommentBtn.on('click',function(e){
    var reason = $complaintCommentsContent.val();
    var appealableId = $('#landing-comments-complaint-modal').attr('data-id');
    if (complaintSending) {
      return;
    }
    var appealType = $complainCommentType.dropdown('get value');
    var formData = new FormData();
    formData.append('appeal_type_id', appealType);
    formData.append('reason', reason);
    formData.append('appeal_type','Note');
    formData.append('target_id',appealableId);
    $.ajax({
      type: 'POST',
      url: "/appeals",
      cache: false,
      contentType: false,
      processData: false,
      data: formData,
      beforeSend: function() {
        setCommentSendStatus(true);
      },
      success: function(res) {
        if (res.status == 200) {
          setCommentSendTip(true);
          setTimeout(function() {
            $complaintCommentsModal.modal('hide');
            restoreCommonentDefault();
          }, 3000);
        }
        setCommentSendStatus(false);
      },
      error: function(err) {
        showCommonTips(err.responseJSON.message, 'error');
        setCommentSendStatus(false);
      }
    })
  });
  
  function showCommonTips(text, type) {
    $complaintModalTip.text(text).show();
    if (type == 'error') {
      $complaintModalTip.removeClass('success').addClass('error');
    } else {
      $complaintModalTip.removeClass('error').addClass('success');
    }
  }
  
  function setCommentSendStatus(value) {
    complaintSending = value;
    if (complaintSending) {
      $complaintCommentBtn.addClass('loading');
      $complaintCommentsContent.attr('readonly', true);
      $complainCommentType.attr('readonly', true);
    } else {
      $complaintCommentBtn.removeClass('loading');
      $complaintCommentsContent.attr('readonly', false);
      $complainCommentType.attr('readonly', false);
    }
  }
  
  function setCommentSendTip(value) {
    if (value) {
      $('.appeal-success-tip').removeClass('hide');
      $('.appeal-tip').addClass('hide');
      $('.appeal-form').addClass('hide');
      $('#landing-comments-complaint-modal .actions').addClass('hide');
    } else {
      $('.appeal-success-tip').addClass('hide');
      $('.appeal-tip').removeClass('hide');
      $('.appeal-form').removeClass('hide');
      $('#landing-comments-complaint-modal .actions').removeClass('hide');
    }
  }
</script>

<div class='ui small modal' id='misjudgment_appeal_modal'>
<i class='close icon'></i>
<div class='header dividing ui'>
误判申诉
</div>
<div class='content'>
<p>此处可能存在不合适展示的内容，页面不予展示。您可通过相关编辑功能自查并修改。</p>
<p>如您确认内容无涉及 不当用语 / 纯广告导流 / 暴力 / 低俗色情 / 侵权 / 盗版 / 虚假 / 无价值内容或违法国家有关法律法规的内容，可点击提交进行申诉，我们将尽快为您处理。</p>
<div class='buttons'>
<div class='ui button blank cancel'>取消</div>
<div class='ui button orange submit'>提交</div>
</div>
</div>
</div>
<style>
  #misjudgment_appeal_modal .buttons {
    float: right;
    margin-top: 30px;
    margin-bottom: 20px; }
    #misjudgment_appeal_modal .buttons .cancel {
      margin-right: 20px; }
</style>
<script>
  var $misjudgmentAppealModal = $('#misjudgment_appeal_modal');
  $('.cancel').on('click',function(){
    $misjudgmentAppealModal.modal('hide');
  });
  var $jsSubmitAppeal = $misjudgmentAppealModal.find('.submit')
  $jsSubmitAppeal.on('click', function(e) {
    e.preventDefault();
    $(this).addClass('loading').addClass('disabled');
    var type = $(this).attr('data-type');
    var id = $(this).attr('data-id');
    var projectId = $(this).attr('data-project-id');
    var appealType = $(this).attr('data-appeal-type');
    $.ajax({
      type: "PUT",
      url: "/misjudgment_appeal",
      data: {
        type: type,
        id: id,
        project_id: projectId,
        appeal_type: appealType
      },
      success: function(data) {
        Flash.info('提交成功');
        $jsSubmitAppeal.removeClass('loading');
        $misjudgmentAppealModal.modal('hide');
        location.reload()
      },
      error: function(e) {
        Flash.error('提交失败:'+e.responseText);
        $jsSubmitAppeal.removeClass('loading').removeClass('disabled');
        location.reload()
      }
    });
  })
</script>

</div>
<script>
  "use strict";
  $('.js-check-star').checkbox('set unchecked')
</script>

</div>
</div>
</div>
<div class='four wide column' style='display: none;'>
<div class='project__right-side'>
<div class='side-item intro'>
<div class='header'>
<h4>简介</h4>
</div>
<div class='content'>
<span class='git-project-desc-text'>一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。</span>
<a class='hide spread' href='javascript:void(0);'>
展开
<i class='caret down icon'></i>
</a>
<a class='retract hide' href='javascript:void(0);'>
收起
<i class='caret up icon'></i>
</a>
<div class='intro-list'>
<div class='blank d-flex d-flex-between dropdown item js-project-label_show label-list-line-feed project-label-list ui' data-labels='[]' data-url='/xuxueli0323/xxl-job/update_description'>
<div class='mixed-label'>
</div>

<div class='default'>暂无标签</div>
</div>
<div class='item'>
<i class='iconfont icon-link'></i>
<span class='git-project-homepage'>
<a rel="nofollow" id="homepage" target="_blank" href="http://www.xuxueli.com/xxl-job/">http://www.xuxueli.com/xxl-job/</a>
</span>
</div>
<div class='item'>
<i class='iconfont icon-tag-program'></i>
<span class='summary-languages'>
Java
<span class='text-muted'>
等 2 种语言
<i class='icon dropdown'></i>
</span>
</span>
<div class='ui popup summary-languages-popup'>
<div class='row'>
<div class='lang'>
<a href="/explore/all?lang=Java">Java</a>
</div>
<div class='lang-bar'>
<div class='bar' style='width: 99.9%;'></div>
</div>
<a class="percentage" href="/explore/all?lang=Java">99.9%</a>
</div>
<div class='row'>
<div class='lang'>
<a href="/explore/all?lang=Dockerfile">Dockerfile</a>
</div>
<div class='lang-bar'>
<div class='bar' style='width: 0.1%;'></div>
</div>
<a class="percentage" href="/explore/all?lang=Dockerfile">0.1%</a>
</div>
</div>
</div>

<div class='item'>
<i class='iconfont icon-licence'></i>
<a target="_blank" id="license-popup" href="/xuxueli0323/xxl-job/blob/master/LICENSE">GPL-3.0</a>
<div class='ui popup dark'>使用 GPL-3.0 开源许可协议</div>
</div>
<div class='item'>
<i class='iconfont icon-apidoc'></i>
ApiDoc：
<a target="_blank" href="https://apidoc.gitee.com/xuxueli0323/xxl-job">apidoc.gitee.com/xuxueli0323/xxl-job</a>
</div>
</div>
</div>
<div class='content intro-form'>
<div class='ui small input'>
<textarea name='project[description]' placeholder='描述' rows='5'></textarea>
</div>
<div class='ui small input'>
<input data-regex-value='(^$)|(^(http|https):\/\/(([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5]).*)|(^(http|https):\/\/[a-zA-Z0-9]+([_\-\.]{1}[a-zA-Z0-9]+)*\.[a-zA-Z]{2,10}(:[0-9]{1,10})?(\?.*)?(\/.*)?$)' name='project[homepage]' placeholder='主页(eg: https://gitee.com)' type='text'>
</div>
<button class='ui orange button mt-1 btn-save'>
保存更改
</button>
<div class='ui blank button btn-cancel-edit'>
取消
</div>
</div>
</div>
<div class='side-item release'>
<div class='header'>
<h4>发行版</h4>
</div>
<div class='content'>
<span class='text-muted'>
暂无发行版
</span>
</div>
</div>
<div class='side-item radar'>
<div class='header mb-1'>
<h4 class='limit-length'>xxl-job</h4>
<a class="ui link button radar-qa" href="javascript:void(0);"><i class='iconfont icon-help-circle'></i>
</a></div>
<div class='content'>
<div data-url='/xuxueli0323/xxl-job/project_radars' id='metrics-radar'>
<div class='wrap skeleton'>
<div class='total-score hide'>
<div class='text'></div>
<div class='score'></div>
</div>
</div>
<div class='ui popup radar-popup'>
<h4 class='title'>Gitee 指数包含如下维度</h4>
<div class='project-radar-list'>
<div class='descript-contianer'>
<div class='descript-title'>
<p>代码活跃度</p>
<p>社区活跃度</p>
<p>团队健康</p>
<p>流行趋势</p>
<p>影响力</p>
</div>
<div class='descript'>
<p>：与代码提交频次相关</p>
<p>：与项目和用户的issue、pr互动相关</p>
<p>：与团队成员人数和稳定度相关</p>
<p>：与项目近期受关注度相关</p>
<p>：与项目的star、下载量等社交指标相关</p>
</div>
</div>
</div>
<div class='finaltime'></div>
</div>
</div>
<script src="https://cn-assets.gitee.com/assets/skill_radar/rep_app-145010700aea13172f33e6c1c7df08c2.js"></script>

</div>
</div>
<div class='side-item contrib' data-url='/xuxueli0323/xxl-job/contributors_count?ref=master' id='contributor'>
<div class='header'>
<h4>
贡献者
<span class='text-muted' id='contributor-count'></span>
</h4>
<a class="ui link button pull-right" href="/xuxueli0323/xxl-job/contributors?ref=master">全部</a>
</div>
<div class='content' id='contributor-list'></div>
<div class='ui active centered inline loader' id='contributor-loader'></div>
</div>
<div class='side-item events' data-url='/xuxueli0323/xxl-job/events.json' id='proj-events'>
<div class='header'>
<h4>近期动态</h4>
</div>
<div class='content'>
<div class='ui comments' id='event-list'></div>
<a class="loadmore hide" href="javascript:void(0);">加载更多
<i class='icon dropdown'></i>
</a><center>
<div class='text-muted nomore hide'>不能加载更多了</div>
<div class='ui inline loader active'></div>
</center>
</div>
</div>
</div>
<div class='ui modal tiny' id='edit-project-description'>
<i class='iconfont icon-close close'></i>
<div class='header'>编辑仓库简介</div>
<div class='content'>
<div class='item mb-2'>
<div class='title label'>简介内容</div>
<div class='ui small input'>
<textarea maxlength='200' name='project[description]' placeholder='描述' rows='5'>一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。</textarea>
</div>
</div>
<div class='item mb-2'>
<div class='title label'>主页</div>
<div class='ui small input'>
<input data-regex-value='(^$)|(^(http|https):\/\/(([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5]).*)|(^(http|https):\/\/[a-zA-Z0-9]+([_\-\.]{1}[a-zA-Z0-9]+)*\.[a-zA-Z]{2,10}(:[0-9]{1,10})?(\?.*)?(\/.*)?$)' name='project[homepage]' placeholder='主页(eg: https://gitee.com)' type='text' value='http://www.xuxueli.com/xxl-job/'>
</div>
</div>
</div>
<div class='actions'>
<button class='ui button blank cancel'>取消</button>
<button class='ui button orange btn-save'>保存更改</button>
</div>
</div>

<script>
  window.gon.projectRightSide = {
    homepage: "http://www.xuxueli.com/xxl-job/",
    description: "一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。",
    url: '/xuxueli0323/xxl-job/update_description',
    i18n: {
      invalidHomepage: '不是有效的 http 地址',
      descriptionLimitExceeded: '简介长度不得超过%{limit}个字符',
      noDescription: '暂无描述',
      noPermission: '无权限操作！',
      requestError: '修改发生错误，请稍后重试！'
    }
  }
  window.gon.cloneArrSelectedLabel = [] || []
  $(function () {
    var $editModal = $('#edit-project-description')
    $editModal.modal({
      onShow: function () {
        window.globalUtils.getFocus($editModal.find('textarea'))
      }
    })
    $('.project__right-side').on('click', '.header .btn-edit', function () {
      $editModal.modal('show')
    })
    $('#license-popup').popup({ position: 'bottom center', lastResort: 'bottom center' })
  
    $('.js-project-label_show').projectLabel({
      i18n: {
        empty: "标签名不能为空",
        verify: "标签名只允许包含中文、字母、数字或者中划线(-)，不能以中划线开头，且长度少于35个字符",
        max: "最多选择 5 个标签"
      }
    })
  })
</script>

</div>
</div>
</div>
<script>
  (function() {
    $(function() {
      Tree.init();
      return TreeCommentActions.init();
    });
  
  }).call(this);
</script>

</div>
<script>
  (function() {
    var donateModal;
  
    Gitee.modalHelper = new GiteeModalHelper({
      alertText: '提示',
      okText: '确定'
    });
  
    donateModal = new ProjectDonateModal({
      el: '#project-donate-modal',
      alipayUrl: '/xuxueli0323/xxl-job/alipay',
      wepayUrl: '/xuxueli0323/xxl-job/wepay',
      nameIsBlank: '名称不能为空',
      nameTooLong: '名称过长（最多为 36 个字符）',
      modalHelper: Gitee.modalHelper
    });
  
    if (null === 'true') {
      donateModal.show();
    }
  
    $('#project-donate').on('click', function() {
      return donateModal.show();
    });
  
  }).call(this);
</script>
<script>
  Tree.initHighlightTheme('white')
</script>


</div>
<div class='gitee-project-extension'>
<div class='extension lang'>Java</div>
<div class='extension public'>1</div>
<div class='extension https'>https://gitee.com/xuxueli0323/xxl-job.git</div>
<div class='extension ssh'>git@gitee.com:xuxueli0323/xxl-job.git</div>
<div class='extension namespace'>xuxueli0323</div>
<div class='extension repo'>xxl-job</div>
<div class='extension name'>xxl-job</div>
<div class='extension branch'>master</div>
</div>

<script>
  $(function() {
    GitLab.GfmAutoComplete.dataSource = "/xuxueli0323/xxl-job/autocomplete_sources"
    GitLab.GfmAutoComplete.Emoji.assetBase = '/assets/emoji'
    GitLab.GfmAutoComplete.setup();
  });
</script>

<footer id='git-footer-main'>
<div class='ui container'>
<div class='logo-row'>
<a href="https://gitee.com"><img alt='Gitee — 基于 Git 的代码托管和研发协作平台' class='logo-img' src='/static/images/logo-black.svg?t=158106666'>
</a></div>
<div class='name-important'>
深圳市奥思网络科技有限公司版权所有
</div>
<div class='ui two column grid d-flex-center'>
<div class='nine wide column git-footer-left'>
<div class='ui four column grid' id='footer-left'>
<div class='column'>
<div class='ui link list'>
<div class='item'>
<a class="item" href="/all-about-git">Git 大全</a>
</div>
<div class='item'>
<a class="item" rel="nofollow" href="https://oschina.gitee.io/learn-git-branching/">Git 命令学习</a>
</div>
<div class='item'>
<a class="item" rel="nofollow" href="https://copycat.gitee.com/">CopyCat 代码克隆检测</a>
</div>
<div class='item'>
<a class="item" href="/appclient">APP与插件下载</a>
</div>
</div>
</div>
<div class='column'>
<div class='ui link list'>
<div class='item'>
<a class="item" href="/gitee_reward">Gitee Reward</a>
</div>
<div class='item'>
<a class="item" href="/gitee-stars">Gitee 封面人物</a>
</div>
<div class='item'>
<a class="item" href="/gvp">GVP 项目</a>
</div>
<div class='item'>
<a class="item" rel="nofollow" href="https://blog.gitee.com/">Gitee 博客</a>
</div>
<div class='item'>
<a class="item" href="/enterprises#nonprofit-plan">Gitee 公益计划</a>
</div>
<div class='item'>
<a class="item" href="https://gitee.com/features/gitee-go">Gitee 持续集成</a>
</div>
</div>
</div>
<div class='column'>
<div class='ui link list'>
<div class='item'>
<a class="item" href="/api/v5/swagger">OpenAPI</a>
</div>
<div class='item'>
<a class="item" href="https://help.gitee.com">帮助文档</a>
</div>
<div class='item'>
<a class="item" href="/self_services">在线自助服务</a>
</div>
<div class='item'>
<a class="item" href="/help/articles/4378">更新日志</a>
</div>
</div>
</div>
<div class='column'>
<div class='ui link list'>
<div class='item'>
<a class="item" href="/about_us">关于我们</a>
</div>
<div class='item'>
<a class="item" rel="nofollow" href="https://www.oschina.net/news/131099/oschina-hiring">加入我们</a>
</div>
<div class='item'>
<a class="item" href="/terms">使用条款</a>
</div>
<div class='item'>
<a class="item" href="/oschina/git-osc/issues">意见建议</a>
</div>
<div class='item'>
<a class="item" href="/links.html">合作伙伴</a>
</div>
</div>
</div>
</div>
</div>
<div class='seven wide column right aligned followus git-footer-right'>
<div class='qrcode mini_app'>
<img alt="微信小程序" src="https://cn-assets.gitee.com/assets/mini_app-e5eee5a21c552b69ae6bf2cf87406b59.jpg" />
<p class='mini_app-text'>微信小程序</p>
</div>
<div class='qrcode weixin'>
<img alt="微信服务号" src="https://cn-assets.gitee.com/assets/qrcode-weixin-9e7cfb27165143d2b8e8b268a52ea822.jpg" />
<p class='weixin-text'>微信服务号</p>
</div>
<div class='phone-and-qq column'>
<div class='ui list official-support-container'>
<div class='item'>
<a class="icon-popup" title="点击加入 Gitee 官方群" rel="nofollow" href="//qm.qq.com/cgi-bin/qm/qr?k=FOdoYurYb10aXeAiViAgsqWX0fsgykNZ"><i class='iconfont icon-logo-qq'></i>
<span>官方技术交流QQ群：777320883</span>
</a></div>
<div class='item mail-and-zhihu'>
<a rel="nofollow" href="mailto: git@oschina.cn"><i class='iconfont icon-msg-mail'></i>
<span id='git-footer-email'>git#oschina.cn</span>
</a></div>
<div class='item mail-and-zhihu'>
<a target="_blank" rel="nofollow" href="https://www.zhihu.com/org/ma-yun-osc/"><i class='iconfont icon-zhihu'></i>
<span>Gitee</span>
</a></div>
<div class='item tel'>
<a>
<i class='iconfont icon-tel'></i>
<span>售前及售后使用咨询：400-606-0201</span>
</a>
</div>
</div>
</div>
</div>
</div>
</div>
<div class='bottombar'>
<div class='ui container'>
<div class='ui d-flex d-flex-between'>
<div class='seven wide column partner d-flex'>
<div class='open-atom d-flex-center'>
<img class="logo-openatom mr-1" alt="开放原子开源基金会" src="https://cn-assets.gitee.com/assets/logo-openatom-d083391cc8a54e283529f3fc11cc38ca.svg" />
<a target="_blank" rel="nofollow" href="https://www.openatom.org/">开放原子开源基金会</a>
<div class='sub-title ml-1'>合作代码托管平台</div>
</div>
<div class='report-12377 d-flex-center ml-3'>
<img class="report-12377__logo mr-1" alt="违法和不良信息举报中心" src="https://cn-assets.gitee.com/assets/12377@2x-1aa42ed2d2256f82a61ecf57be1ec244.png" />
<a target="_blank" rel="nofollow" href="https://12377.cn">违法和不良信息举报中心</a>
</div>
<div class='copyright ml-3'>
<a rel="nofollow" href="http://beian.miit.gov.cn/">粤ICP备12009483号</a>
</div>
</div>
<div class='nine wide column right aligned'>
<i class='icon world'></i>
<a href="/language/zh-CN">简 体</a>
/
<a href="/language/zh-TW">繁 體</a>
/
<a href="/language/en">English</a>
</div>
</div>
</div>
</div>
</footer>

<script>
  var officialEmail = $('#git-footer-email').text()
  $('#git-footer-main .icon-popup').popup({ position: 'bottom center' })
  $('#git-footer-email').text(officialEmail.replace('#', '@'))
  window.gon.popover_card_locale = {
    follow:"关注",
    unfollow:"已关注",
    gvp_title: "GVP - Gitee 最有价值开源项目",
    project: "项目",
    org: "开源组织",
    member: "",
    author: "作者",
    user_blocked: "该用户已被屏蔽或已注销",
    net_error: "网络错误",
    unknown_exception: "未知异常"
  }
  window.gon.select_message = {
    placeholder: "请输入个人空间地址或完整的邮箱地址"
  }
</script>
<script src="https://cn-assets.gitee.com/webpacks/popover_card-d30978018805efc377e9.bundle.js"></script>
<link rel="stylesheet" media="all" href="https://cn-assets.gitee.com/webpacks/css/gitee_nps-69491f94919350b0258c.css" />
<script src="https://cn-assets.gitee.com/webpacks/gitee_nps-548cf00696f895086765.bundle.js"></script>
<script src="https://cn-assets.gitee.com/webpacks/gitee_icons-4c841b120ded010873f2.bundle.js"></script>


<div class='side-toolbar'>
<div class='button toolbar-help'>
<i class='iconfont icon-help'></i>
</div>
<div class='ui popup left center dark'>点此查找更多帮助</div>
<div class='toolbar-help-dialog'>
<div class='toolbar-dialog-header'>
<h3 class='toolbar-dialog-title'>搜索帮助</h3>
<form class="toolbar-help-search-form" action="/help/load_keywords_data" accept-charset="UTF-8" method="get"><input name="utf8" type="hidden" value="&#x2713;" />
<div class='ui icon input fluid toolbar-help-search'>
<input name='keywords' placeholder='请输入产品名称或问题' type='text'>
<i class='icon search'></i>
</div>
</form>

<i class='iconfont icon-close toolbar-dialog-close-icon'></i>
</div>
<div class='toolbar-dialog-content'>
<div class='toolbar-help-hot-search'>
<div class='toolbar-roll'>
<a class="init active" title="Git 命令在线学习" href="https://oschina.gitee.io/learn-git-branching/?utm_source==gitee-help-widget"><i class='Blue icon icon-command iconfont'></i>
<span>Git 命令在线学习</span>
</a><a class="init " title="如何在 Gitee 导入 GitHub 仓库" href="https://gitee.com/help/articles/4261?utm_source==gitee-help-widget"><i class='icon icon-clipboard iconfont orange'></i>
<span>如何在 Gitee 导入 GitHub 仓库</span>
</a></div>
<div class='toolbar-list'>
<div class='toolbar-list-item'>
<a href="/help/articles/4114">Git 仓库基础操作</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4166">企业版和社区版功能对比</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4191">SSH 公钥设置</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4194">如何处理代码冲突</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4232">仓库体积过大，如何减小？</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4279">如何找回被删除的仓库数据</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4283">Gitee 产品配额说明</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4284">GitHub仓库快速导入Gitee及同步更新</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4328">什么是 Release（发行版）</a>
</div>
<div class='toolbar-list-item'>
<a href="/help/articles/4354">将 PHP 项目自动发布到 packagist.org</a>
</div>
</div>
</div>
<div class='toolbar-help-search-reseult'></div>
</div>
</div>
<script>
  var opt = { position: 'left center'};
  var $helpSideToolbar = $('.button.toolbar-help');
  var $toolbarRoll = $('.toolbar-roll');
  
  $(function() {
    if (false) {
      $helpSideToolbar.popup(opt).popup({lastResort:'left center'})
    } else {
      $helpSideToolbar.popup({lastResort:'left center'}).popup('show', opt);
      setTimeout(function() {
        $helpSideToolbar.popup('hide', opt);
      }, 3000);
    }
  
    if ($toolbarRoll.length) {
      setInterval(function() {
        var $nextActiveLink = $toolbarRoll.find('a.active').next();
        if (!$nextActiveLink.length) {
          $nextActiveLink = $toolbarRoll.find('a:first-child');
        }
        $nextActiveLink.attr('class', 'active').siblings().removeClass('active init');
      }, 5000);
    }
  })
</script>

<div class='popup button' id='home-comment'>
<i class='iconfont icon-comment'></i>
</div>
<div class='ui popup dark'>评论</div>
<div class='toolbar-appeal popup button'>
<i class='iconfont icon-report'></i>
</div>
<div class='ui popup dark'>
仓库举报
</div>
<script>
  $('.toolbar-appeal').popup({ position: 'left center' });
</script>

<div class='button gotop popup' id='gotop'>
<i class='iconfont icon-top'></i>
</div>
<div class='ui popup dark'>回到顶部</div>
</div>
<div class='form modal normal-modal tiny ui' id='unlanding-complaint-modal'>
<i class='iconfont icon-close close'></i>
<div class='header'>
登录提示
</div>
<div class='container actions'>
<div class='content'>
该操作需登录 Gitee 帐号，请先登录后再操作。
</div>
<div class='ui orange icon large button ok'>
立即登录
</div>
<div class='ui button blank cancel'>
没有帐号，去注册
</div>
</div>
</div>
<script>
  var $elm = $('.toolbar-appeal');
  
  $elm.on('click', function() {
    var modals = $("#unlanding-complaint-modal.normal-modal");
    if (modals.length > 1) {
      modals.eq(0).modal('show');
    } else {
      modals.modal('show');
    }
  })
  $("#unlanding-complaint-modal.normal-modal").modal({
    onDeny: function() {
      window.location.href = "/signup?from=";
    },
    onApprove: function() {
      window.location.href = "/login?from=";
    }
  })
</script>

<style>
  .side-toolbar .bdsharebuttonbox a {
    font-size: 24px;
    color: white !important;
    opacity: 0.9;
    margin: 6px 6px 0px 6px;
    background-image: none;
    text-indent: 0;
    height: auto;
    width: auto;
  }
</style>
<style>
  #udesk_btn a {
    margin: 0px 20px 167px 0px !important;
  }
</style>
<script>
  (function() {
    $('#project-user-message').popup({
      position: 'left center'
    });
  
  }).call(this);
</script>
<script>
  Gitee.initSideToolbar({
    hasComment: true,
    commentUrl: '/xuxueli0323/xxl-job#tree_comm_title'
  })
</script>





<script>
  (function() {
    this.__gac = {
      domain: 'www.oschina.net'
    };
  
  }).call(this);
</script>

<script src="https://cn-assets.gitee.com/assets/bdstatic/app-070a9e339ac82bf2bf7ef20375cd4121.js"></script>
<script src="https://cn-assets.gitee.com/webpacks/build_status-a3ee4cc8489b2defc1a8.bundle.js"></script>
<script src="https://cn-assets.gitee.com/webpacks/scan_status-12043c7d32460905e204.bundle.js"></script>
<script src="https://cn-assets.gitee.com/webpacks/mermaid_render-7a8ec62c3ce489559313.bundle.js"></script>
</body>
</html>
