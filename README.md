<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>财神计划团队 - 鸿运彩票</title>
    <!--
	<script type="text/javascript">var cnzz_protocol = (("https:" == document.location.protocol) ? " https://" : " http://");document.write(unescape("%3Cspan id='cnzz_stat_icon_1275755960'%3E%3C/span%3E%3Cscript src='" + cnzz_protocol + "s23.cnzz.com/z_stat.php%3Fid%3D1275755960' type='text/javascript'%3E%3C/script%3E"));</script>
    
-->
    <link rel="stylesheet" href="m/css/m.css" tppabs="http://119.42.34.43:8085/m/css/m.css">
    <style>
        .qq-canvas {
            width: 16ex;
            top: 35%;
        }
    </style>
    <script>
        var _hmt = _hmt || [];
        (function () {
            var hm = document.createElement("script");
            hm.src = "../hm.baidu.com/hm.js-3f6e006f81a637c10f8d0af7aaf3d90d"/*tpa=https://hm.baidu.com/hm.js?3f6e006f81a637c10f8d0af7aaf3d90d*/;
            var s = document.getElementsByTagName("script")[0];
            s.parentNode.insertBefore(hm, s);
        })();
    </script>
</head>

<body>
    <div class="bg">
        <div style="width: 100%; height: 10px;">
        </div>
        <div class="header">
        </div>

        <div id="content-canvas">
        </div>
        <script type="text/template" id="content-template">
            <div class="content">
                <div class='wx'>导师QQ: <span id="wx">{wechat}</span></div>
                <div class='teach'>我在导师(<span id='name'>{name}</span>)指导月收入<span>{money}万</span></div>
                <div id='text1' class='text'>{tip1}</div>
                <div id='text2' class='text'>{tip2}</div>
                <div id='text3' class='text'>{tip3}</div>
            </div>

            <div class="qr-canvas">
                <div class='code'>
                    <img style="width: 100%; height: 100%" src="{qr_url}" />
                </div>
                <div class='qr-text' id="copy-btn">
                    点此复制QQ号
                </div>
                <div class='qr-text'>
                    <a href="{sign_url}" target="_blank">立即注册</a>
                </div>
            </div>
        </script>
        <div class='qq-canvas' id='imgDiv'>
            <div class='title'>绝密内部计划群</div>
            <ul id='qq-canvas'>
            </ul>
            <script type='text/template' id='qq-template'>
                <li>
                    <a href="{url}"  class='qq-style' >
                        <div class='qq-logo'></div>
                        <span class='qq-title'>点击加群</span>
                    </a>
                </li>
            </script>
        </div>
    </div>
</body>
<script src="js/jquery-1.9.1.min.js" tppabs="http://119.42.34.43:8085/js/jquery-1.9.1.min.js"></script>
<!-- <script src='./js/clipboard.min.js'></script> -->
<script src="js/data.js" tppabs="http://119.42.34.43:8085/js/data.js"></script>
<script>
    var random_item = data[Math.floor(Math.random() * data.length)];
    // var clipboard = new ClipboardJS('#copy-btn', {
    //     text: function () {
    //         var num = ''
    //         if (Number(random_item['is_wx'])) {
    //             num = random_item['wechat'];
    //         } else {
    //             num = random_item['qq']
    //         }
    //         var wechat_num = num.trim();
    //         return wechat_num;
    //     }
    // });

    // clipboard.on('success', function (e) {
    //     alert('复制成功');
    // });


    var arr = [];

    function fill_content(data) {
        var html = $("#content-template").html();
        var list = [];

        $.each(data, function (index, val) {
            list.push(formatTemplate(val, html));
        });
        $('#content-canvas').empty();
        $('#content-canvas').append(list.join(''));
    }

    function formatTemplate(dta, tmpl) {
        var format = {
            name: function (x) {
                return x
            }
        };
        return tmpl.replace(/{(\w+)}/g, function (m1, m2) {
            if (!m2)
                return "";
            return (format && format[m2]) ? format[m2](dta[m2]) : dta[m2];
        });
    }

    function fill_init_data() {
        var isMobile = /(?:Android|iPad|PlayBook|iPhone|SymbianOS|Phone|Mobile)/i.test(navigator.userAgent);
        arr = [];
        var qq_grup_arr = [];
        var random_item = data[Math.floor(Math.random() * data.length)];
        arr.push(random_item);
        fill_content(arr);
        if (random_item['qq_arr'] && random_item['qq_arr'].length != 0) {
            $.each(random_item['qq_arr'], function (i, item) {
                item['url'] = "mqqapi://card/show_pslcard?src_type=internal&version=1&uin=" + item[
                        'qq_number'] +
                    "&card_type=group&source=qrcode";
                qq_grup_arr.push(item);
            });
            qq_content(qq_grup_arr);
        } else {
            $('.qq-canvas').hide();
        }
    }

    fill_init_data();


    function qq_content(data) {
        var html = $("#qq-template").html();
        var list = [];

        $.each(data, function (index, val) {
            list.push(formatTemplate(val, html));
        });
        $('#qq-canvas').empty();
        $('#qq-canvas').append(list.join(''));
    }
    // 复制微信
    function copywx() {
        const range = document.createRange();
        range.selectNode(document.getElementById('wx'));
        const selection = window.getSelection();
        if (selection.rangeCount > 0) selection.removeAllRanges();
        selection.addRange(range);
        document.execCommand('copy');
        alert("复制成功！");
    }
    $(function () {
        if (Number(random_item['is_wx'])) {
            var html = "<div class='wx'>导师微信: <span id='wx'>" + random_item['wechat'] + "</span></div>"
            $('.wx').html(html);
            $('#copy-btn').text('点此复制微信');
            $('#copy-btn').click(function () {
                copywx()
                window.location.href = "weixin://";
            });
        } else {
            var html = "<div class='wx'>导师QQ: <span id='wx'>" + random_item['qq'] + "</span></div>"
            $('.wx').html(html);
            $('#copy-btn').text('点此复制QQ号');
            $('#copy-btn').click(function () {
                copywx();
                jump_qq(random_item['qq']);
            });
        }        
    })
    function jump_qq(qq) {
        var isMobile = /(?:Android|iPad|PlayBook|iPhone|SymbianOS|Phone|Mobile)/i.test(navigator.userAgent);
        if (isMobile) {
            var url = 'mqq://im/chat?chat_type=wpa&uin=' + qq + '&version=1&src_type=web';
            window.location.href = url;
        } else {
            var url = 'tencent://message/?Menu=yes&uin=' + qq +
                '&Site=80fans&Service=300&sigT=45a1e5847943b64c6ff3990f8a9e644d2b31356cb0b4ac6b24663a3c8dd0f8aa12a545b1714f9d45';
            window.open(url);
        }
    }
</script>
<script>
    var xin = true,
        yin = true;
    var step = 1;
    var delay = 20;
    var $obj;
    $(function () {
        $obj = $("#imgDiv");
        var time = window.setInterval("move()", delay);
        $obj.mouseover(function () {
            clearInterval(time)
        });
        $obj.mouseout(function () {
            time = window.setInterval("move()", delay)
        });
    });

    function move() {
        var left = $obj.offset().left;
        var top = $obj.offset().top;
        var L = T = 0; //左边界和顶部边界
        var R = $(window).width() - $obj.width(); // 右边界
        var B = $(window).height() - $obj.height(); //下边界

        //难点:怎样判断广告的4个边框有没有超出可视化范围!
        if (left < L) {
            xin = true; // 水平向右移动
        }
        if (left > R) {
            xin = false;
        }
        if (top < T) {
            yin = true;
        }
        if (top > B) {
            yin = false;
        }
        //根据有没有超出范围来确定广告的移动方向
        left += step * (xin == true ? 1 : -1);
        top += step * (yin == true ? 1 : -1);
        // 给div 元素重新定位
        $obj.offset({
            top: top,
            left: left
        })
    }
    //关闭
    $(function () {
        $("#a").click(function () {
            var b = $("#a").parent();
            $(b).remove();
        })
    })
</script>

</html>