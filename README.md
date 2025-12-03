<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <title>⚠️ 보안 경고</title>
  <style>
    :root { --red:#ff0033; --bg:#000; --yellow:#ffea00; }
    * { box-sizing:border-box; }
    body {
      margin:0; height:100vh; display:flex; flex-direction:column; justify-content:center; align-items:center;
      background:var(--bg); color:var(--yellow); font-family:Consolas,monospace; text-align:center;
    }
    h1{ font-size:clamp(2rem,6vw,4rem); margin:0 0 1rem; color:var(--red); animation:flash 1s infinite alternate; }
    p { font-size:clamp(1rem,2.5vw,1.5rem); max-width:90vw; line-height:1.5; margin:0; }
    @keyframes flash{ from{opacity:.7;} to{opacity:1;} }
    #count{font-size:2rem;margin-top:1.5rem;color:var(--red);}  
  </style>
</head>
<body>
  <h1>⚠️ XSS 취약점 테스트 페이지</h1>
  <p>
    본 페이지는 <strong>XSS(크로스사이트 스크립팅)</strong> 공격 시나리오를 시각적으로 경고하기 위한 데모입니다.<br>
    웹 서비스  이용중 강제 리다이렉트되어 이 화면이 나타났더라도, 이는 모의해킹 취약점 점검을 위한 테스트용 페이지일 뿐이며 <br><strong>실제 악성 코드 실행 및 데이터 수집은 수행되지 않습니다.</strong><br>
    <br>
    <span style="color:#aaa;">※ 실제 정보 수집은 이루어지지 않았으며, 취약점 검증 목적의 경고 화면입니다.</span>
  </p>
  <div id="count">5</div>
  <span style="color:#aaa;">이전 페이지로 이동합니다.</span>

<script>
(() => {
  const redirectTo = 'https://google.com';  // 필요시 변경
  let n = 5;
  const el = document.getElementById('count');
  const tick = () => {
    n--; if(n<=0){ location.href = redirectTo; return; }
    el.textContent = n; setTimeout(tick,1000);
  };
  setTimeout(tick,1000);
})();
</script>
</body>
</html>

