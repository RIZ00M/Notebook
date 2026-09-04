**Change Element ID To Link**
<script>

document.querySelectorAll('#demo').forEach(function(el) {

&#x20;   const link = document.createElement('a');

&#x20;   link.href = 'https://example.com';

&#x20;   link.textContent = el.textContent;

&#x20;   el.replaceWith(link);

});

</script>

