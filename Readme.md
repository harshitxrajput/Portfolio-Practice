# AdvanceProject

## Overview
This project is a visually appealing portfolio website showcasing the skills and projects of a MERN stack web developer. It features smooth animations, interactive elements, and a modern design.

## Functionality
- **Hero Section**: Displays the developer's name, title, and availability with smooth text animations.
- **Projects Section**: Highlights key projects with hover effects that reveal project images and animations.
- **About Section**: Provides a brief introduction about the developer.
- **Footer**: Contains links to social media profiles and additional information.

## Animations
### GSAP (GreenSock Animation Platform)
- **Text Animations**: The `firstPageAnim` function animates the navigation bar and hero section text with fade-in and slide-up effects.
- **Hover Effects**: Project images appear with opacity and rotation changes when hovered over.
- **Mouse Movement Effects**: The `circleMouseFollower` function creates a dynamic mini-circle that follows the cursor with scaling effects.

### Locomotive Scroll
- **Smooth Scrolling**: The `LocomotiveScroll` library is used to enable smooth scrolling throughout the website, enhancing the user experience.

## Code Usage
### JavaScript
The main animations and interactivity are implemented in `script.js`:
```javascript
// filepath: c:\Users\Harshit\Desktop\Web Development\Projects\AdvanceProject\script.js
const scroll = new LocomotiveScroll({
    el: document.querySelector('#main'),
    smooth: true
});

function firstPageAnim() {
    let tl = gsap.timeline();
    tl.from("#nav", { y: '-10', opacity: 0, duration: 1.5, ease: Expo.easeInOut })
      .to(".boundingelem", { y: 0, ease: Expo.easeInOut, duration: 2, delay: -1, stagger: .3 })
      .from("#hero-down", { y: -10, opacity: 0, duration: 1.5, delay: -1, ease: Expo.easeInOut });
}

function circleSkew() {
    let xscale = 1, yscale = 1, xprev = 0, yprev = 0;
    window.addEventListener("mousemove", function(dets) {
        this.clearTimeout(timeout);
        xscale = gsap.utils.clamp(.8, 1.2, dets.clientX - xprev);
        yscale = gsap.utils.clamp(.8, 1.2, dets.clientY - yprev);
        xprev = dets.clientX;
        yprev = dets.clientY;
        circleMouseFollower(xscale, yscale);
        timeout = setTimeout(() => {
            document.querySelector("#minicircle").style.transform = `translate(${dets.clientX}px, ${dets.clientY}px) scale(1, 1)`;
        }, 100);
    });
}

function circleMouseFollower(xscale, yscale) {
    window.addEventListener('mousemove', function(dets) {
        document.querySelector("#minicircle").style.transform = `translate(${dets.clientX}px, ${dets.clientY}px) scale(${xscale}, ${yscale})`;
    });
}

firstPageAnim();
circleSkew();
```

### CSS
The styles for the animations and layout are defined in `style.css`:
```css
/* filepath: c:\Users\Harshit\Desktop\Web Development\Projects\AdvanceProject\style.css */
/* ...existing code... */
#minicircle {
    width: 10px;
    height: 10px;
    background-color: #fff;
    position: absolute;
    z-index: 9999;
    border-radius: 50%;
    transition: all cubic-bezier(0.19, 1, 0.22, 1) 0.4s;
}
/* ...existing code... */
.bounding .boundingelem {
    transform: translateY(100%);
}
/* ...existing code... */
```

### HTML
The structure of the website is defined in `index.html`:
```html
<!-- filepath: c:\Users\Harshit\Desktop\Web Development\Projects\AdvanceProject\index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- ...existing code... -->
</head>
<body>
    <div id="minicircle"></div>
    <div id="main">
        <div id="hero">
            <div id="nav">
                <a href>Harshit Rajput</a>
                <h4>MENU+</h4>
            </div>
            <!-- ...existing code... -->
        </div>
        <!-- ...existing code... -->
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.7/gsap.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/locomotive-scroll@3.5.4/dist/locomotive-scroll.min.js"></script>
    <script src="script.js"></script>
</body>
</html>
```

## Libraries Used
- **GSAP**: For animations.
- **Locomotive Scroll**: For smooth scrolling.

## How to Run
1. Clone the repository.
2. Open `index.html` in a browser.
3. Ensure an internet connection for external libraries (GSAP and Locomotive Scroll).

## Future Enhancements
- Add more projects to the portfolio.
- Implement a contact form for direct communication.
- Optimize for mobile responsiveness.
