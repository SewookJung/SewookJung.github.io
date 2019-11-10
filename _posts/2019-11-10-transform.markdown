---
layout: post
---

# transform 적용 후 다시 원상복귀 하는 방법

HTML, CSS 공부 중 삽질을 한 부분을 포스팅 해보려고 합니다. <br>
처음 기술 포스팅을 하는 부분이라 부족한 요소가 많아도 이해바랍니다.

## 1. transform이란?

- CSS의 시각적 서식 모델(visual formatting model)의 좌표 공간을 변형시킬 수 있다<br> 해당 속성에 지정된 값에 따라 엘리먼트(element)에 이동(translate), 회전(rotate), 크기변경(scale), 기울임(skew)등의 효과를 줄 수 있다. [ - (출처) transform-MDN](https://developer.mozilla.org/ko/docs/Web/CSS/transform)

## 2. 기능 시나리오

- input 클릭
- input Y축을 기점으로 약 -100px 이동
- 글자 입력 완료 후 input position 원상복귀<br>

## 3. 문제점

- input 클릭 후 정상적으로 Y축을 -100px 옮기는데는 성공 했으나<br>
  typing 완료 후 input이 부자연스럽게 원상복구 됨

- 문제의 코드 <br>
  이걸 한시간 넘게 고쳐보려고 노력을..ㅋㅋ

    <center>
    <div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">.chat__write&nbsp;</span>{<span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;trasnform</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;translateY(0px)</span><span style="color:#ff3399">;</span><span style="color:#0066cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0066cc"></span>}<span style="color:#ff3399"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">.chat__write</span><span style="color:#4DA51B">:focus&nbsp;</span><span style="color:#ff3399"></span>{<span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;transform</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;translateY(-100px)</span><span style="color:#ff3399">;</span><span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;transition</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;transform&nbsp;1s&nbsp;ease</span><span style="color:#ff3399">;</span><span style="color:#0066cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0066cc"></span>}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
    </center>
    <br>

## 4. 문제의 코드 고치기!

<center>
<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">.chat__write&nbsp;</span>{<span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;transition</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;transform&nbsp;1s&nbsp;ease</span><span style="color:#ff3399">;</span><span style="color:#0066cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0066cc"></span>}<span style="color:#ff3399"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">.chat__write</span><span style="color:#4DA51B">:focus&nbsp;</span><span style="color:#ff3399"></span>{<span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;transform</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;translateY(-100px)</span><span style="color:#ff3399">;</span><span style="color:#0099cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0099cc">&nbsp;&nbsp;transition</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;transform&nbsp;1s&nbsp;ease</span><span style="color:#ff3399">;</span><span style="color:#0066cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0066cc"></span>}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
</center>

- transform에 꽂혀서 계속 이것만 세팅을 했다.. <br>
  사실 transition을 사용하면 끝나는 부분을 한시간을 넘게 삽질을 하였다.. <br>
  내가 정확히 transition에 대한 개념이 부족했으니 이런 결과가 나온 것 같다..

- 설명
  - <span style="color:#ff3399">.chat\_\_write</span><span style="color:#4DA51B">:focus&nbsp;</span>는 transition 기능을 사용해서 input이 이동될때 부드럽게 이동된다.
  - <span style="color:#ff3399">.chat\_\_write</span><span style="color:#4DA51B"></span> 또한 transition 기능을 추가하여 transform 되었던 부분을 부드럽게 원상복구 시켜준다.

## 5. transition이란?

- CSS 트랜지션은 CSS 속성을 변경할 때 애니메이션 속도를 조절하는 방법을 제공합니다 <br>
  [ - (출처) transition-MDN](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)

## 6. 총 평

- 마무리하면서 생각해보니 transform과 transition은 뗄레야 뗄 수 없는 존재 같다.<br>
  간단하게 설명하자면 <strong><u>transform은 이동, 회전, 기울기 등을 설정</u></strong>하고 <strong><u>transition이 변경되는 부분의 애니메이션 속도를 조절하는 기능</u></strong>이라고 생각하면 된다.

---

처음 포스팅 해보는 거라 많은 부분이 미숙하고 정보 전달이 정확히 어렵네요..ㅠㅠ 댓글기능도 추가하도록 하겠습니다. 만약 제가 틀린 부분이 있다면 수정 요청 부탁드립니다 ㅎㅎ
