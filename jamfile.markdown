---
layout: default
title: "**"
permalink: /mt/
---

<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>

<input id="pass-input" type="text"/>
<button id="check-btn">Pedo mellon a minno</button>

<div id="subscribe-form" style="display:none; margin-top:20px;">
  <h2>Subscribe to Updates</h2>
  <form id="subscription-form">
    <label for="preferred-name">Preferred Name:</label><br>
    <input type="text" id="preferred-name" name="preferred-name" required placeholder="你的昵称/Preferred name" /><br><br>
    <label for="email">Your Email:</label><br>
    <input type="email" id="email" name="email" required placeholder="阿达西@鹏油.edu" /><br><br>
    <button type="submit">Subscribe</button>
  </form>
  <div id="status" style="margin-top:10px;"></div>
</div>

<script>

  document.getElementById('check-btn').addEventListener('click', function() {
    var val = document.getElementById('pass-input').value.trim();
    if (val === '鹏油') {
      document.getElementById('subscribe-form').style.display = 'block';

      emailjs.send('service_4xhhvn5', 'template_a0iqdka', {
        unlocker: 'Someone',
        passphrase: val,
        to_email: 'timmotaffy@gmail.com'
      });
    } else {
      document.getElementById('subscribe-form').style.display = 'none';
      document.getElementById('pass-input').value = '';
    }
  });

  // EmailJS 配置
  emailjs.init('W6HQtTfTgchY3l70B');

  document.getElementById('subscription-form').addEventListener('submit', function(e) {
    e.preventDefault();
    const email = document.getElementById('email').value;
    const preferredName = document.getElementById('preferred-name').value;
    const status = document.getElementById('status');

    // 邮箱格式校验
    var emailPattern = /^[^@\s]+@[^@\s]+\.[^@\s]+$/;
    if (!emailPattern.test(email)) {
      status.textContent = 'Invalid email format.';
      status.style.color = 'orange';
      return;
    }

    status.textContent = 'Subscribing...';

    emailjs.send('service_4xhhvn5', 'template_a0iqdka', {
      subscriber_email: email,
      preferred_name: preferredName,
      to_email: 'timmotaffy@gmail.com'
    })
    .then(function() {
      status.textContent = 'Successfully subscribed! 🎉';
      status.style.color = 'green';
      document.getElementById('email').value = '';
      document.getElementById('preferred-name').value = '';

      // 发送确认邮件给订阅者
      emailjs.send('service_4xhhvn5', 'template_confirmation', {
        subscriber_email: email,
        preferred_name: preferredName,
        to_email: email
      })
      .then(function() {
        console.log('Confirmation email sent to subscriber.');
      })
      .catch(function(err) {
        console.error('Confirmation email error:', err);
      });

      // 3秒后关闭山洞的门（隐藏表单，回到密钥界面）
      setTimeout(function() {
        document.getElementById('subscribe-form').style.display = 'none';
        document.getElementById('pass-input').value = '';
      }, 3000);
    })
    .catch(function(error) {
      status.textContent = 'Subscription failed. Please try again.';
      status.style.color = 'red';
      console.error('EmailJS error:', error);
    });
  });
</script>
