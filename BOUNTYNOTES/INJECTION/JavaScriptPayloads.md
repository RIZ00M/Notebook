# JavaScript Injection Payloads

## Change Element ID To Link

Replaces the content of every element with `id="demo"` with a clickable link, keeping the original text as the link text.

```html
<script>
document.querySelectorAll('#demo').forEach(function(el) {
    const link = document.createElement('a');
    link.href = 'https://example.com';
    link.textContent = el.textContent;
    el.replaceWith(link);
});
</script>
```
