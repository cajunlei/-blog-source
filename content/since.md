---
title: "我　们"
---

{{< css-since >}}

### 我们已经在一起

<div id="clockdiv">
  <div>
    <p id="y2"></p>
    <div class="smalltext">Years</div>
  </div>
  <div>
    <p id="d2"></p>
    <div class="smalltext">Days</div>
  </div>
  <div>
    <p id="h2"></p>
    <div class="smalltext">Hours</div>
  </div>
  <div>
    <p id="i2"></p>
    <div class="smalltext">Minutes</div>
  </div>
  <div>
    <p id="s2"></p>
    <div class="smalltext">Seconds</div>
  </div>
</div>

###### Hold your hands till the end of my life


<br>

<hr>

<br>

<script>
  var countDownDate1 = new Date('2020-11-12T00:00:00').getTime();
  window.setInterval(function() {
    var distance1 = new Date().getTime() - countDownDate1;
    var year1 = Math.floor(distance1 / (1000 * 60 * 60 * 24 * 365));
    var days1 = Math.floor(distance1 / (1000 * 60 * 60 * 24) - 365);
    var hours1 = Math.floor((distance1 % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    var minutes1 = Math.floor((distance1 % (1000 * 60 * 60)) / (1000 * 60));
    var seconds1 = Math.floor((distance1 % (1000 * 60)) / 1000);
    document.getElementById("y2").innerHTML = year1;
    document.getElementById("d2").innerHTML = days1;
    document.getElementById("h2").innerHTML = hours1;
    document.getElementById("i2").innerHTML = minutes1;
    document.getElementById("s2").innerHTML = seconds1;
  }, 1000);
</script>

