To fix the error and ensure the password visibility toggle works correctly, you need to make sure that the script targets the correct password input field and eye icon. Here's the corrected and enhanced JavaScript code:

```javascript
// visibility of the password and the functionality
// of the show password icon
document.querySelectorAll(".infield i").forEach((toggleBtn) => {
    toggleBtn.addEventListener('click', () => {
        const pswrdfield = toggleBtn.previousElementSibling;
        if (pswrdfield.type === "password") {
            pswrdfield.type = "text";  
            toggleBtn.classList.add("active");
        } else {
            pswrdfield.type = "password";
            toggleBtn.classList.remove("active");
        }
    });
});
```

This code ensures that each eye icon correctly toggles the visibility of its corresponding password input field, even if there are multiple password fields on the page. It uses `querySelectorAll` to select all eye icons and adds event listeners to each of them. The `previousElementSibling` property is used to get the input field associated with the clicked eye icon.
