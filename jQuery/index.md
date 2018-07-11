# 내가 선택한 태그의 인덱스 값 찾기

```html
<head>
    <script type="text/javascript">
        $(function () {
            $(".btn").click(function () {
                var index = $(".btn").index(this);

                // 각 버튼을 누르면 해당되는 index의 레이어를 출력시킨다.
                // 단, 다른 영역들은 닫혀야 하고 클릭된 영역만 보여주어야 한다.
                $(".layer").hide();
                $(".layer").eq(index).show();
            })
        })
    </script>
</head>

<body>
    <input type="button" class="btn" value="버튼1" />
    <input type="button" class="btn" value="버튼2" />
    <input type="button" class="btn" value="버튼3" />
    <div class="layer" style="display: none;">
        레이어1입니다.
        <br/> 레이어1입니다.
        <br/> 레이어1입니다.
        <br/> 레이어1입니다.
        <br/> 레이어1입니다.
        <br/> 레이어1입니다.
    </div>
    <div class="layer" style="display: none;">
        레이어2입니다.
        <br/> 레이어2입니다.
        <br/> 레이어2입니다.
        <br/> 레이어2입니다.
        <br/> 레이어2입니다.
        <br/> 레이어2입니다.
    </div>
    <div class="layer" style="display: none;">
        레이어3입니다.
        <br/> 레이어3입니다.
        <br/> 레이어3입니다.
        <br/> 레이어3입니다.
        <br/> 레이어3입니다.
        <br/> 레이어3입니다.
    </div>
</body>

```