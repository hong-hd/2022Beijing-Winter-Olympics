# hellow-world
just another respository
<!DCOTYPE html>
    <html lang="en">

    <head>
        <meta charset="utf-8" />
        <title>2022年北京冬奥会</title>
        <script src="scripts/modernizr.js"></script>

        <link rel="stylesheet" type="text/css" href="styles/color.css" charset="utf-8">
        <link rel="stylesheet" type="text/css" href="styles/layout.css" charset="utf-8">
        <link rel="stylesheet" type="text/css" href="styles/typography.css" charset="utf-8">
        <style>
            .snow {
                color: white;
                animation: rotes 3s infinite linear;
            }

            @keyframes rotes {
                100% {
                    transform: rotate3d(1, -1, 1, 720deg);
                }
            }
        </style>

    </head>

    <body>
        <header>
            <img src="images/logo.gif" alt="2022年北京冬奥会" />
            <nav>
                <ul>
                    <li><a href="北京冬奥会.html" class="here">Home</a></li>
                    <li><a href="about.html">About</a></li>
                    <li><a href="photos.html">Photos</a></li>
                    <li><a href="former.html">Former</a></li>
                    <li><a href="contact.html">Contact</a></li>
                </ul>
            </nav>
        </header>
        <article>
            <h1>北京欢迎你</h1>
            <p id="intro">
                Welcome to Beijing</br>
                여러분의 북경 </br>
                Добро пожаловать в Пекин</br>
                </br>
                在这里你可以<a href="about.html" title="About">更好的了解2022年北京冬奥会，</a>
                在这里你可以<a href="photos.html" title="Photos">看到照片剪影，</a>
                在这里你可以<a href="former.html" title="Live">了解冬奥会的历史，</a>
                在这里你可以<a href="contact.html" title="Contact">留下你想说的话。</a>
            </p>
        </article>
        <script src="scripts/global.js"></script>
        <script src="scripts/xuehua.js"></script>
    </body>

    </html>

    <script type="text/javascript">
        snow = function () {
            this.body = document.body;
            this.millisec = 30;
            this.timer;
            this.winwidth = window.innerWidth;
            this.winHeight = window.innerHeight;

            this.create = function () {
                snowborder = document.createElement('div');
                snow = document.createElement('div');
                snowborder.appendChild(snow);
                snowborder.style.position = 'absolute';

                snow.classList.add('snow');
                snow.innerHTML = '❉';
                return snowborder;
            }
            this.play = function () {
                this.body.style.cssText = `transform-style:preserve-3d;
transform:perspective(50rem);`;
                var that = this;
                this.timer = setInterval(function () {
                    var snowborder = that.create();
                    var cloneSnow = snowborder.cloneNode(1);
                    var startx = (that.winwidth * .95) * Math.random();
                    var starty = (that.winHeight * .95) * Math.random();
                    var endx = (that.winwidth * .95) * Math.random();
                    var endy = (that.winHeight * .95) * Math.random();
                    var endz = (that.winHeight * .5) * Math.random();
                    var duration = parseInt(4000 + Math.random() * 4000);
                    var fontSize = 1 + Math.random() * 30;
                    var startOpacity = .5 + .3 * Math.random();
                    var endOpacity = .1;
                    cloneSnow.style.cssText += `
transform:translate3d(${startx}px,0,${endz}px);
opacity:${startOpacity};
transition:all ${duration}ms linear;
font-size:${fontSize}px;`;
                    that.body.appendChild(cloneSnow);
                    setTimeout(function () {
                        cloneSnow.style.cssText += `
transform:translate3d(${endx}px,${endy}px,${endz}px);
opacity:${endOpacity};
`;
                        setTimeout(function () {
                            cloneSnow.remove();
                        }, duration);
                    }, 100);
                }, this.millisec);
                return "play";
            };
            this.stop = function () {
                clearInterval(this.timer);
                return 'stop';
            }
        }
        snowObject = new snow();
        snowObject.play(); 
    </script>
