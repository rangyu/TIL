# Phaser 3 시작하기 (Hello World)

(Phaser3과 Phaser2는 코드 차이가 크다. 이 글은 phaser3을 기준으로 한다.)

## Phaser 설치하기

### 다운로드

* Phaser 다운로드 링크 : https://phaser.io/download/stable

### CDN

```html
<script src="//cdn.jsdelivr.net/npm/phaser@3.16.2/dist/phaser.js"></script>
<script src="//cdn.jsdelivr.net/npm/phaser@3.16.2/dist/phaser.min.js"></script>
```

## Hello World

```html
<!DOCTYPE html>
<html>
<head>
    <script src="https://cdn.jsdelivr.net/npm/phaser@3.15.1/dist/phaser-arcade-physics.min.js"></script>
</head>
<body>

    <script>
    var config = {
        type: Phaser.AUTO,
        width: 800,
        height: 600,
        physics: {
            default: 'arcade',
            arcade: {
                gravity: { y: 200 }
            }
        },
        scene: {
            preload: preload,
            create: create
        }
    };

    var game = new Phaser.Game(config);

    function preload ()
    {
        this.load.setBaseURL('http://labs.phaser.io');

        this.load.image('sky', 'assets/skies/space3.png');
        this.load.image('logo', 'assets/sprites/phaser3-logo.png');
        this.load.image('red', 'assets/particles/red.png');
    }

    function create ()
    {
        this.add.image(400, 300, 'sky');

        var particles = this.add.particles('red');

        var emitter = particles.createEmitter({
            speed: 100,
            scale: { start: 1, end: 0 },
            blendMode: 'ADD'
        });

        var logo = this.physics.add.image(400, 100, 'logo');

        logo.setVelocity(100, 200);
        logo.setBounce(1, 1);
        logo.setCollideWorldBounds(true);

        emitter.startFollow(logo);
    }
    </script>

</body>
</html>
```
(출처 : https://phaser.io/tutorials/getting-started-phaser3/part5)