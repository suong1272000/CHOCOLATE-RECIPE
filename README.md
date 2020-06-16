<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <title>CHOCOLATE RECIPE</title>
    <style type="text/css">
        html,body{ margin:0; padding:0; width:1920px; height:100%;}
        .box{ width:960px; height:1080px; position:relative; color:#ffffff; font-size:24pt;}
		h1 {
			font-size: 126pt; color: #512413; font-family: Jalnan;
		}
    </style>
    <script type="text/javascript" src="http://code.jquery.com/jquery-1.12.4.min.js"></script>
    <script type="text/javascript">
        window.onload = function () {
            var elm = ".box";
            $(elm).each(function (index) {
                // 개별적으로 Wheel 이벤트 적용
                $(this).on("mousewheel DOMMouseScroll", function (e) {
                    e.preventDefault();
                    var delta = 0;
                    if (!event) event = window.event;
                    if (event.wheelDelta) {
                        delta = event.wheelDelta / 120;
                        if (window.opera) delta = -delta;
                    } 
                    else if (event.detail)
                        delta = -event.detail / 3;
                    var moveTop = $(window).scrollTop();
                    var elmSelecter = $(elm).eq(index);
                    // 마우스휠을 위에서 아래로
                    if (delta < 0) {
                        if ($(elmSelecter).next() != undefined) {
                            try{
                                moveTop = $(elmSelecter).next().offset().top;
                            }catch(e){}
                        }
                    // 마우스휠을 아래에서 위로
                    } else {
                        if ($(elmSelecter).prev() != undefined) {
                            try{
                                moveTop = $(elmSelecter).prev().offset().top;
                            }catch(e){}
                        }
                    }
                     
                    // 화면 이동 0.8초(800)
                    $("html,body").stop().animate({
                        scrollTop: moveTop + 'px'
                    }, {
                        duration: 800, complete: function () {
                        }
                    });
                });
            });
        }
    </script>
</head>
<body>
    <div class="box">
		<img src="images/PAGE02-수정_01.jpg">
		<h1>CHOCOLATE RECIPE</h1>
	</div>
    <div class="box">
		<img src="images/PAGE02-수정_02.jpg">
		</div>
    <div class="box">
		<div>
		<img src="images/PAGE02-수정_03.jpg">
	</div>	
	</div>

</body>
</html>
