<html>
<head>
    <title>Your Portfolio</title>
    <style>
        /* Add your CSS here */
        body {
            color: white;
            background: black;
            overflow: hidden;
        }
    </style>
</head>
<body>
    <canvas id="matrixRain"></canvas>

    <div id="content">
        <!-- Add your content here -->
        <h1>Welcome to My Portfolio</h1>
    </div>

    <script>
        // Add your JavaScript here
        var canvas = document.getElementById('matrixRain');
        var ctx = canvas.getContext('2d');

        canvas.height = window.innerHeight;
        canvas.width = window.innerWidth;

        var matrixSymbols = "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%";
        matrixSymbols = matrixSymbols.split("");

        var font_size = 10;
        var columns = canvas.width/font_size;

        var drops = [];
        for(var x = 0; x < columns; x++)
            drops[x] = 1; 

        function drawMatrixRain()
        {
            ctx.fillStyle = "rgba(0, 0, 0, 0.04)";
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = "#0F0"; 
            ctx.font = font_size + "px arial";
            for(var i = 0; i < drops.length; i++)
            {
                var text = matrixSymbols[Math.floor(Math.random()*matrixSymbols.length)];
                ctx.fillText(text, i*font_size, drops[i]*font_size);

                if(drops[i]*font_size > canvas.height && Math.random() > 0.975)
                    drops[i] = 0;

                drops[i]++;
            }
        }

        setInterval(drawMatrixRain, 33);
    </script>
</body>
</html>
