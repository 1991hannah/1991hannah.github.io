  <script>
    (function () {
      var form = document.getElementById('signup-form');
      var emailInput = document.getElementById('email');
      var message = document.getElementById('form-message');
      var emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

      form.addEventListener('submit', function (event) {
        event.preventDefault();
        message.className = 'message';
        message.textContent = '';

        var email = emailInput.value.trim();

        if (!email || !emailPattern.test(email)) {
          message.className = 'message error';
          message.textContent = 'Please enter a valid email address.';
          emailInput.focus();
          return;
        }

        // Simulate a successful signup (replace with real backend/service call)
        message.className = 'message success';
        message.textContent = 'You\u2019re on the list! We\u2019ll be in touch soon.';
        emailInput.value = '';
      });
    })();
  </script>
