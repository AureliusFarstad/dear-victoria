<script>
    // No need for 'onMount' or imports for SSR compatibility
</script>

<div class="letter-container">
    <div class="greeting">
        <p>Dear Victoria,</p>
    </div>

    <div class="message">
        <p>You are the most beautiful person I have ever met. You are the most caring, loving, and supportive person I have ever known. You have an incredible way of seeing the world and others within it.</p>
    </div>

    <!-- Glowing Pinpoint -->
    <div class="glowing-point">
        <div class="glowing-light"></div>
    </div>

    <div class="message">
        <p>It seems to me like your family has kindled a passionate flame in your heart. And every day you stoke it with your meditations, empathy, and love. Now it shines so strongly and every day you use it to brighten the lives of those around you.</p>
    </div>

    <div class="message">
        <p>You embody the giving spirit of Christmas every day of the year. You give your time and physical presence to those in need through your volunteer work. You give your big brains to those in need through your research and Elnor. You give your love to all your friends and family. You give everyone the benefit of the doubt, always pursuing mercy and forgiveness. You give me so much joy and love always.</p>
    </div>

    <div class="message">
        <p>Thank you for taking me on so many wonderful adventures this year. Colombia was incredibly special - and to have you as my tour guide was the best part. I loved every moment of our time together in Cartagena, Bogota, and the coffee region. I'm excited for the new year and the possibilities we might have to go there again. Italy was pretty amazing too with you and your family there to show me all the best places. Thank you and them for making me feel so welcome. Norway was fun too - you brightened the dark days of winter and embraced the cold with me. In the Summer, you were so patient with me and my sickness - thank you for that too. Then there were our trips around Greece. Thank you for being spontaneous with me. I'm so grateful for all the memories we've made together and excited for the ones we will make in the future.</p>
    </div>

    <div class="message">
        <p>You were amazing this year - Moving to Greece with a stress-free attitude, getting the Fulbright grant, passing your proposal exam, growing Elnor, supporting not only Glocal Roots but the whole VCC! You blow me away with your ambition, intelligence, and drive. I'm so proud of you and all you've accomplished. I hope you take this Christmas time to relax and feel good about all you've done this year. You deserve it.</p>
    </div>

    <div class="message">
        <p>You are a gift to me and to the world. I love you so much.</p>
    </div>

    <div class="signature">
        <p>Merry Christmas with lots of cheesy love from Marcus.</p>
    </div>
</div>

<!-- Snowfall Overlay -->
<div class="snowflakes">
    <div class="snowflake" style="animation-delay: 0s;"></div>
    <div class="snowflake" style="animation-delay: 1s;"></div>
    <div class="snowflake" style="animation-delay: 2s;"></div>
    <div class="snowflake" style="animation-delay: 3s;"></div>
    <div class="snowflake" style="animation-delay: 4s;"></div>
    <!-- Add more snowflakes if you want a denser effect -->
</div>

<style>
body {
    background-color: rgb(170, 222, 223); /* Light warm background */
    color: #333; /* Dark text color for readability */
    line-height: 1.6;
    padding: 20px;
    margin: 0;
    position: relative; /* To position snowflakes over the content */
    overflow-x: hidden; /* Prevent snowflakes from going off screen horizontally */
}

/* Container for the letter content */
.letter-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: rgb(218, 250, 250); /* Light warm background */
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    font-family: 'Georgia', serif; /* Elegant serif font */
}

/* Glowing Pinpoint of Light */
.glowing-point {
    position: relative;
    width: 100%;
    height: 100px; /* Adjust for positioning */
    display: flex;
    justify-content: center;
    align-items: center;
}

.glowing-light {
    width: 30px;
    height: 30px;
    background-color: #d4af37; /* Elegant golden color */
    border-radius: 50%;
    box-shadow: 0 0 20px #d4af37, 0 0 30px #d4af37, 0 0 40px #d4af37;
    position: absolute;
    animation: pulse 1.5s infinite alternate;
}

/* Glowing effect animation */
@keyframes pulse {
    0% {
        transform: scale(1);
        opacity: 1;
    }
    100% {
        transform: scale(1.5);
        opacity: 0.5;
    }
}

/* Snowflakes falling animation */
.snowflakes {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none; /* Makes snowflakes non-interactive */
    z-index: 10; /* Ensures snowflakes are above content */
}

.snowflake {
    position: absolute;
    top: -10px;
    background-color: #fff;
    width: 5px;
    height: 5px;
    border-radius: 50%;
    opacity: 0.8;
    animation: fall 10s linear infinite, sway 3s ease-in-out infinite;
}

/* Snowflake falling animation */
@keyframes fall {
    0% {
        top: -10px;
    }
    100% {
        top: 100%;
    }
}

/* Snowflakes swaying animation (adds movement in the wind) */
@keyframes sway {
    0% {
        left: 0%;
    }
    50% {
        left: 50%;
    }
    100% {
        left: 0%;
    }
}

/* Glowing effect on greeting */
.greeting p {
    font-size: 2rem;
    font-weight: bold;
    text-align: center;
    color: #d4af37; /* Elegant golden color */
}

/* Apply a subtle glowing effect to the closing text */
.closing p {
    font-size: 1.2rem;
    font-weight: bold;
    margin-top: 20px;
    text-align: center;
    color: #d4af37;
}

.signature p {
    font-size: 1rem;
    text-align: center;
    font-style: italic;
    color: #333;
    margin-top: 20px;
}

/* General message styles */
.message p {
    font-size: 1.2rem;
    margin-bottom: 15px;
    text-align: justify;
    color: #555;
}
</style>
