To achieve the desired functionality with your HTML, CSS, and JavaScript, you need to ensure that the transitions between the sign-up and sign-in forms are smooth and the overlay panels switch content appropriately. Here's an updated version of your code:

### HTML File
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sign in || Sign up form</title>
     <!-- font awesome icons -->
     <link rel="stylesheet" href="../fontawesome-free-6.2.1-web/css/all.css">
    <!-- css stylesheet -->
    <link rel="stylesheet" href="./style.css">
</head>
<body>

    <div class="container" id="container">
        <div class="form-container sign-up-container">
            <form action="#">
                <h1>Create Account</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your email for registration</span>
                <div class="infield">
                    <input type="text" placeholder="Name" required>
                    <label></label>
                </div>
                <div class="infield">
                    <input type="email" placeholder="Email" name="email" required>
                    <label></label>
                </div>
                <div class="infield">
                    <input type="password" placeholder="Password" required>
                    <i id="eye" class="fas fa-eye"></i>
                    <label></label>
                </div>
                <button>Sign Up</button>
            </form>
        </div>
        <div class="form-container sign-in-container">
            <form action="#">
                <h1>Sign in</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your account</span>
                <div class="infield">
                    <input type="email" placeholder="Email" name="email" required>
                    <label></label>
                </div>
                <div class="infield">
                    <input type="password" name="password" placeholder="Password" minlength="8" maxlength="16" required>
                    <i id="eye" class="fas fa-eye"></i>
                    <label></label>
                </div>
                <a href="#" class="forgot">Forgot your password?</a>
                <button>Log In</button>
            </form>
        </div>
        <div class="overlay-container" id="overlayCon">
            <div class="overlay">
                <div class="overlay-panel overlay-left">
                    <h1>Welcome Back!</h1>
                    <p>To keep connected with us please login with your personal info</p>
                    <button id="signIn">Sign In</button>
                </div>
                <div class="overlay-panel overlay-right">
                    <h1>Hello, Friend!</h1>
                    <p>Enter your personal details and start journey with us</p>
                    <button id="signUp">Create an account</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- js code -->
    <script src="./script.js"></script>

</body>
</html>
```

### CSS File
```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

* {
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
}

:root {
    --linear-grad: linear-gradient(to right, #141E30, #243B55);
    --grad-clr1: #141E30;
    --grad-clr2: #243B55;
}

body {
    height: 100vh;
    background: #f6f5f7;
    display: grid;
    place-content: center;
    font-family: 'Poppins', sans-serif;
}

.container{
    position: relative;
    width: 850px;
    height: 500px;
    background: #fff;
    box-shadow: 25px 30px 55px #5557;
    border-radius: 13px;
    overflow: hidden;
}

.form-container {
    position: absolute;
    width: 50%;
    height: 100%;
    padding: 8px 40px;
    transition: all 0.6s ease-in-out;
}

.sign-up-container{
    left: 100%;
    opacity: 0;
    z-index: 1;
}

.sign-in-container{
    left: 0;
    opacity: 1;
    z-index: 2;
}

.container.signup-mode .sign-up-container{
    left: 0;
    opacity: 1;
    z-index: 5;
}

.container.signup-mode .sign-in-container{
    left: -100%;
    opacity: 0;
    z-index: 1;
}

form{
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 8px 50px;
}

h1{
    color: var(--grad-clr1);
}

.social-container{
    margin: 20px 0px;
}

.social-container a{
    border: 1px solid #ddd;
    border-radius: 50%;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    margin: 0px 5px;
    height: 40px;
    width: 40px;
}

.social-container a:hover{
    color: #fff;
    background-color: var(--grad-clr1);
}

span{
    font-size: 12px;
}

.infield{
    position: relative;
    margin: 8px 0px;
    width: 100%;
}

.input{
    width: 100%;
    padding: 12px 15px;
    background: #f3f3f3;
    border: none;
    outline: none;
}

label{
    position: absolute;
    left: 50%;
    top: 100%;
    transform: translate(-50%);
    width: 100%;
    height: 2px;
    background: var(--linear-grad);
    transition: 0.3s;
}

input{
    width: 100%;
    padding: 13px;
    outline: none;
    color: var(--grad-clr1);
    /* border: none; */
}

/* showing psd  */

    
.infield i{
    position: absolute;
    right: 15px;
    color: var(--grad-clr1);
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
    background-color: #fff;
    padding: 8px;
}

.infield i.active::before{
    color: var(--grad-clr1);
    content: "\f070";
}

.infield i:hover{
    color: #001;
}


a{
    color: #333;
    font-size: 14px;
    text-decoration: none;
    margin: 15px 0px;
}

a.forgot:hover{
    padding-bottom: 3px;
    transition: .3s ease;
    transition-duration: 1s;
    border-bottom: 2px solid var(--grad-clr2);
}

button{
    border-radius: 10px;
    border: 1px solid var(--grad-clr2); 
    background: var(--grad-clr2);
    color: #fff;
    font-size: 12px;
    font-weight: bold;
    padding: 12px 45px;
    letter-spacing: 1px;
    text-transform: uppercase;
}

.form-container button{
    margin-top: 17px;
    transition: 80ms ease-in;
}

.form-container button:hover{
    background: #fff;
    color: var(--grad-clr1);
}

.overlay-container{
    position: absolute;
    top: 0;
    left: 50%;
    width: 50%;
    height: 100%;
    overflow: hidden;
    transition: transform 0.6s ease-in-out;
    z-index: 100;
}

.overlay{
    background: var(--linear-grad);
    color: #fff;
    position: relative;
    left: -100%;
    width: 200%;
    height: 100%;
    transition: transform 0.6s ease-in-out;
}

.overlay-panel{
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0px 40px;
    text-align: center;
    top: 0;
    height: 100%;
    width: 50%;
    transition: transform 0.6s ease-in-out;
}

.overlay-left{
    transform: translateX(-20%);
}

.overlay-right{
    right: 

0;
    transform: translateX(0);
}

.container.signup-mode .overlay-container{
    transform: translateX(-100%);
}

.container.signup-mode .overlay{
    transform: translateX(50%);
}

.container.signup-mode .overlay-left{
    transform: translateX(0%);
}

.container.signup-mode .overlay-right{
    transform: translateX(20%);
}
```

### JavaScript File (script.js)
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const container = document.getElementById('container');
    const signUpButton = document.getElementById('signUp');
    const signInButton = document.getElementById('signIn');

    signUpButton.addEventListener('click', () => {
        container.classList.add('signup-mode');
    });

    signInButton.addEventListener('click', () => {
        container.classList.remove('signup-mode');
    });
});
```

This code ensures that when you click the "Create an account" button, the overlay slides to reveal the "Welcome Back!" message and sign-in form, and vice versa. The transitions are smooth and consistent with the animation you desire.
