
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sleek Floating Banner</title>
    <style>
        /* Modern CSS reset for consistency */
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            min-height: 200vh; /* Adds scrollable height to visualize the fixed positioning */
            background-color: #121212; /* A dark, neutral background */
            color: #fff;
        }

        /* MAIN FLOATING BANNER CONTAINER
           Fixed to the top center of the screen
        */
        #sleek-floating-banner {
            position: fixed;
            top: 20px; /* Slight offset from the top border */
            left: 50%;
            transform: translateX(-50%); /* Centers horizontally */
            width: 340px; /* Compact, friendly width for desktop/mobile */
            height: 52px;
            background: rgba(30, 30, 30, 0.9); /* Dark semi-transparent background */
            backdrop-filter: blur(10px); /* Modern 'glassmorphism' effect */
            -webkit-backdrop-filter: blur(10px); /* Safari support */
            border: 1px solid rgba(255, 255, 255, 0.1); /* Subtle outline */
            border-radius: 50px; /* Fully rounded edges for a sleek pill look */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5); /* Strong shadow for depth */
            display: flex;
            align-items: center;
            justify-content: space-between; /* Icon+Text on left, button on right */
            padding: 0 6px 0 16px; /* Optimized padding for the components */
            z-index: 10000; /* Ensures it stays above all other content */
            overflow: hidden; /* Needed for the marquee slide effect */
            
            /* Entry animation */
            animation: bannerEntry 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
            opacity: 0;
            transition: all 0.3s ease;
        }

        /* Hover effect to highlight the interactive nature */
        #sleek-floating-banner:hover {
            transform: translateX(-50%) scale(1.03);
            border-color: #FF1493; /* DeepPink border highlight on hover */
        }

        /* Banner entry animation (slides in and bounces slightly) */
        @keyframes bannerEntry {
            from { top: -60px; opacity: 0; }
            to { top: 20px; opacity: 1; }
        }

        /* --- MARQUEE SLIDER STYLES --- */
        .banner-text-slider {
            flex: 1;
            height: 22px; /* Set height to constrain the text */
            overflow: hidden; /* Masks text outside the area */
            position: relative;
            margin-right: 12px;
        }

        .slide-inner {
            display: flex;
            flex-direction: column; /* Stacks text vertically for sliding */
            animation: verticalSlide 8s cubic-bezier(0.645, 0.045, 0.355, 1) infinite;
        }

        /* Text element properties */
        .slide-inner span {
            height: 22px; /* Matches parent height */
            color: rgba(255, 255, 255, 0.9); /* Slightly off-white for better readability */
            font-size: 0.8rem;
            font-weight: 600; /* Semi-bold */
            display: flex;
            align-items: center;
            gap: 8px; /* Gap for the indicator dot */
            white-space: nowrap; /* Prevents text wrapping */
        }

        /* Color highlight for key inscriptions */
        .highlight-text {
            color: #FF1493; /* DeepPink */
        }

        /* Subtle animated dot for live status feel */
        .live-dot {
            width: 7px;
            height: 7px;
            background-color: #FF1493;
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(255, 20, 147, 0.8);
            animation: pulseDot 1.5s infinite;
        }

        /* Pulse animation for the live dot */
        @keyframes pulseDot {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.3; transform: scale(1.2); }
        }

        /* Vertical Slide Keyframes:
           4 states (3 texts + return to 1). 
           Uses percentages to control pause duration at each state.
        */
        @keyframes verticalSlide {
            0%, 22% { transform: translateY(0); } /* Pauses on Text 1 */
            33%, 55% { transform: translateY(-22px); } /* Slides to and Pauses on Text 2 */
            66%, 88% { transform: translateY(-44px); } /* Slides to and Pauses on Text 3 */
            100% { transform: translateY(0); } /* Loops back to Text 1 smoothly */
        }

        /* --- BUTTON STYLES --- */
        .launch-btn {
            background-color: #FF1493; /* Vibrant DeepPink for main color */
            color: #fff;
            padding: 9px 20px;
            border-radius: 25px; /* Rounded pill style to match banner */
            font-size: 0.75rem;
            font-weight: 900; /* Extra bold text for contrast */
            border: none;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-decoration: none; /* Removes underline for <a> tags */
            display: flex;
            align-items: center;
            gap: 6px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3); /* Soft DeepPink glow */
        }

        /* Button interaction effects */
        .launch-btn:hover {
            background-color: #ff50ac; /* Lighter DeepPink on hover */
            transform: translateY(-1px);
            box-shadow: 0 6px 20px rgba(255, 20, 147, 0.5); /* Stronger DeepPink glow */
        }

        .launch-btn:active {
            transform: translateY(1px) scale(0.98); /* Click interaction feedback */
        }

        /* --- SVG ICON STYLE --- */
        .arrow-icon {
            width: 13px;
            height: 13px;
            fill: none;
            stroke: currentColor; /* Matches text color (#fff) */
            stroke-width: 3;
            transition: transform 0.3s ease;
        }

        /* Hover animation specifically for the icon */
        .launch-btn:hover .arrow-icon {
            transform: translateX(3px); /* Arrow nudges right on hover */
        }
    </style>
</head>
<body>

    <div id="sleek-floating-banner" onclick="openHomeLink()">
        <div class="banner-text-slider">
            <div class="slide-inner">
                <span>
                    <div class="live-dot"></div> 
                    DeBeatz<span class="highlight-text">GH</span> Resource Hub
                </span>
                <span>
                    <div class="live-dot"></div>
                    Lifestyle <span class="highlight-text">&</span> Strategy
                </span>
                <span>
                    <div class="live-dot"></div>
                    Latest updates are <span class="highlight-text">Live</span>
                </span>
            </div>
        </div>

        <button class="launch-btn" onclick="openHomeLink(event)">
            OPEN 
            <svg class="arrow-icon" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
        </button>
    </div>

    <script>
        /**
         * Opens the specified URL in a new tab without navigating
         * away from the current page.
         * @param {Event} e - Optional event object to prevent bubbling.
         */
        function openHomeLink(e) {
            // Check if event exists and stop propagation so clicking the button
            // doesn't also trigger the banner's onclick.
            if (e && e.stopPropagation) {
                e.stopPropagation();
            }
            
            // window.open(url, '_blank') opens in a new tab.
            window.open("https://debeatzgh1.github.io/debeatzgh", "_blank");
        }
    </script>

</body>
</html>



<div id="smart-float-container" class="float-wrapper">
    <div id="float-nudge" class="float-nudge">
        <p>Claim your <strong>.wordpress.com</strong> site!</p>
        <button onclick="dismissNudge()" class="nudge-close">×</button>
    </div>

    <div class="float-main-btn" onclick="launchWPSignup()">
        <i class="fab fa-wordpress"></i>
        <span class="btn-label">Create Site</span>
    </div>
</div>

<style>
    .float-wrapper {
        position: fixed;
        bottom: 20px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 12px;
        z-index: 10005;
        font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Floating Nudge Bubble */
    .float-nudge {
        background: rgba(10, 10, 12, 0.9);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(0, 242, 255, 0.3);
        padding: 8px 15px;
        border-radius: 12px;
        color: #f0f6fc;
        font-size: 11px;
        white-space: nowrap;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        display: none; /* Controlled by JS */
        animation: slideUpFade 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        align-items: center;
        gap: 10px;
    }

    .nudge-close {
        background: none;
        border: none;
        color: #64748b;
        font-size: 16px;
        cursor: pointer;
        padding: 0 2px;
        line-height: 1;
    }

    .nudge-close:hover { color: #00f2ff; }

    /* Main Button */
    .float-main-btn {
        background: #00f2ff;
        color: #000;
        padding: 10px 20px;
        border-radius: 99px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        font-weight: 800;
        text-transform: uppercase;
        font-size: 10px;
        letter-spacing: 1px;
        box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        transition: all 0.3s ease;
    }

    .float-main-btn:hover {
        transform: translateY(-3px) scale(1.05);
        background: #fff;
        box-shadow: 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .float-main-btn i { font-size: 14px; }

    @keyframes slideUpFade {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 480px) {
        .float-main-btn { padding: 10px 16px; }
        .btn-label { display: none; } /* On mobile, only show icon to save space */
    }
</style>

<script>
    const NUDGE_KEY = 'wp_nudge_dismissed';

    function showNudge() {
        const isDismissed = localStorage.getItem(NUDGE_KEY);
        if (!isDismissed) {
            document.getElementById('float-nudge').style.display = 'flex';
        }
    }

    function dismissNudge() {
        document.getElementById('float-nudge').style.display = 'none';
        // Remember dismissal for 24h
        localStorage.setItem(NUDGE_KEY, 'true');
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Blogger-sign-up-button-/";
        
        // Use existing overlay logic if available
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-popup nudge after 8 seconds
    window.addEventListener('load', () => {
        setTimeout(showNudge, 8000);
    });
</script>




<div id="smart-float-container" class="float-wrapper">
    <div id="float-nudge" class="float-nudge">
        <p>Home <get more ideas!</p>
        <button onclick="dismissNudge()" class="nudge-close">×</button>
    </div>

    <div class="float-main-btn" onclick="launchWPSignup()">
        <i class="fab fa-wordpress"></i>
        <span class="btn-label">Create Site</span>
    </div>
</div>

<style>
    .float-wrapper {
        position: fixed;
        bottom: 20px;
        left: 10%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 12px;
        z-index: 10005;
        font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Floating Nudge Bubble */
    .float-nudge {
        background: rgba(10, 10, 12, 0.9);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(0, 242, 255, 0.3);
        padding: 8px 15px;
        border-radius: 12px;
        color: #f0f6fc;
        font-size: 11px;
        white-space: nowrap;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        display: none; /* Controlled by JS */
        animation: slideUpFade 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        align-items: center;
        gap: 10px;
    }

    .nudge-close {
        background: none;
        border: none;
        color: #64748b;
        font-size: 16px;
        cursor: pointer;
        padding: 0 2px;
        line-height: 1;
    }

    .nudge-close:hover { color: #00f2ff; }

    /* Main Button */
    .float-main-btn {
        background: #00f2ff;
        color: #000;
        padding: 10px 20px;
        border-radius: 99px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        font-weight: 800;
        text-transform: uppercase;
        font-size: 10px;
        letter-spacing: 1px;
        box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        transition: all 0.3s ease;
    }

    .float-main-btn:hover {
        transform: translateY(-3px) scale(1.05);
        background: #fff;
        box-shadow: 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .float-main-btn i { font-size: 14px; }

    @keyframes slideUpFade {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 480px) {
        .float-main-btn { padding: 10px 16px; }
        .btn-label { display: none; } /* On mobile, only show icon to save space */
    }
</style>

<script>
    const NUDGE_KEY = 'wp_nudge_dismissed';

    function showNudge() {
        const isDismissed = localStorage.getItem(NUDGE_KEY);
        if (!isDismissed) {
            document.getElementById('float-nudge').style.display = 'flex';
        }
    }

    function dismissNudge() {
        document.getElementById('float-nudge').style.display = 'none';
        // Remember dismissal for 24h
        localStorage.setItem(NUDGE_KEY, 'true');
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Home/";
        
        // Use existing overlay logic if available
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-popup nudge after 8 seconds
    window.addEventListener('load', () => {
        setTimeout(showNudge, 8000);
    });
</script>



<div class="separator" style="clear: both;"><a href="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticlogoforadigitaltoolcalledall-in-onefloatinginfomenuforblogger5444122951694103302.jpg" style="display: block; padding: 1em 0; text-align: center; "><img alt="" border="0" width="320" data-original-height="1024" data-original-width="1024" src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticlogoforadigitaltoolcalledall-in-onefloatinginfomenuforblogger5444122951694103302.jpg"/></a></div><!DOCTYPE html>
<html lang="en" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blogger Iframe Embed Generator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        'primary-dark': '#4B4BC8',
                    }
                }
            }
        }
    </script>
</head>
<body class="min-h-full bg-white dark:bg-gray-900 transition-colors duration-200">
    <div class="container mx-auto px-4 py-8 max-w-4xl">
        <!-- Header -->
        <div class="text-center mb-8">
            <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-2">
                Blogger Iframe Generator
            </h1>
            <p class="text-gray-600 dark:text-gray-300 text-lg">
                Generate iframe embed codes for your Blogger posts
            </p>
        </div>

        <!-- Input Section -->
        <div class="bg-gray-50 dark:bg-gray-800 rounded-lg p-6 mb-6 shadow-sm">
            <h2 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">
                URL Input
            </h2>
            
            <div class="space-y-4">
                <div>
                    <label for="urlInput" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                        Website URL
                    </label>
                    <input 
                        type="url" 
                        id="urlInput" 
                        placeholder="https://example.com"
                        class="w-full px-4 py-3 text-base border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent bg-white dark:bg-gray-700 text-gray-900 dark:text-white placeholder-gray-500 dark:placeholder-gray-400 transition-colors"
                    >
                </div>

                <!-- Iframe Options -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div>
                        <label for="widthInput" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                            Width
                        </label>
                        <input 
                            type="text" 
                            id="widthInput" 
                            value="100%"
                            class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent bg-white dark:bg-gray-700 text-gray-900 dark:text-white transition-colors"
                        >
                    </div>
                    <div>
                        <label for="heightInput" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                            Height
                        </label>
                        <input 
                            type="text" 
                            id="heightInput" 
                            value="400"
                            class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent bg-white dark:bg-gray-700 text-gray-900 dark:text-white transition-colors"
                        >
                    </div>
                    <div>
                        <label for="borderInput" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                            Border
                        </label>
                        <select 
                            id="borderInput"
                            class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent bg-white dark:bg-gray-700 text-gray-900 dark:text-white transition-colors"
                        >
                            <option value="0">No Border</option>
                            <option value="1">1px Border</option>
                            <option value="2">2px Border</option>
                        </select>
                    </div>
                </div>

                <!-- Additional Options -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="flex items-center">
                        <input 
                            type="checkbox" 
                            id="allowFullscreen" 
                            checked
                            class="w-4 h-4 text-primary bg-gray-100 border-gray-300 rounded focus:ring-primary dark:focus:ring-primary dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
                        >
                        <label for="allowFullscreen" class="ml-2 text-sm font-medium text-gray-700 dark:text-gray-300">
                            Allow Fullscreen
                        </label>
                    </div>
                    <div class="flex items-center">
                        <input 
                            type="checkbox" 
                            id="responsiveFrame"
                            class="w-4 h-4 text-primary bg-gray-100 border-gray-300 rounded focus:ring-primary dark:focus:ring-primary dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
                        >
                        <label for="responsiveFrame" class="ml-2 text-sm font-medium text-gray-700 dark:text-gray-300">
                            Make Responsive
                        </label>
                    </div>
                </div>

                <button 
                    id="generateBtn"
                    class="w-full md:w-auto px-6 py-3 bg-primary hover:bg-primary-dark text-white font-medium rounded-lg transition-colors duration-200 focus:ring-4 focus:ring-primary/30"
                >
                    Generate Iframe Code
                </button>
            </div>
        </div>

        <!-- Output Section -->
        <div id="outputSection" class="bg-gray-50 dark:bg-gray-800 rounded-lg p-6 mb-6 shadow-sm hidden">
            <div class="flex items-center justify-between mb-4">
                <h2 class="text-xl font-semibold text-gray-900 dark:text-white">
                    Generated Embed Code
                </h2>
                <button 
                    id="copyBtn"
                    class="px-4 py-2 bg-primary hover:bg-primary-dark text-white font-medium rounded-lg transition-colors duration-200 focus:ring-4 focus:ring-primary/30"
                >
                    Copy Code
                </button>
            </div>
            
            <div class="relative">
                <textarea 
                    id="embedCode" 
                    readonly
                    rows="6"
                    class="w-full px-4 py-3 text-sm font-mono bg-white dark:bg-gray-700 border border-gray-300 dark:border-gray-600 rounded-lg text-gray-900 dark:text-white resize-none focus:ring-2 focus:ring-primary focus:border-transparent"
                ></textarea>
            </div>

            <!-- Success Message -->
            <div id="copySuccess" class="mt-3 p-3 bg-green-100 dark:bg-green-900/30 border border-green-400 dark:border-green-600 text-green-700 dark:text-green-400 rounded-lg hidden">
                ✅ Embed code copied to clipboard!
            </div>
        </div>

        <!-- Preview Section -->
        <div id="previewSection" class="bg-gray-50 dark:bg-gray-800 rounded-lg p-6 shadow-sm hidden">
            <h2 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">
                Live Preview
            </h2>
            <div id="previewContainer" class="border border-gray-300 dark:border-gray-600 rounded-lg overflow-hidden">
                <!-- Preview iframe will be inserted here -->
            </div>
        </div>

        <!-- Instructions -->
        <div class="bg-blue-50 dark:bg-blue-900/30 border border-blue-200 dark:border-blue-700 rounded-lg p-6 mt-6">
            <h3 class="text-lg font-semibold text-blue-900 dark:text-blue-300 mb-2">
                How to Use in Blogger
            </h3>
            <ol class="list-decimal list-inside space-y-2 text-blue-800 dark:text-blue-400">
                <li>Copy the generated iframe code above</li>
                <li>In your Blogger post editor, switch to "HTML" view</li>
                <li>Paste the iframe code where you want the embed to appear</li>
                <li>Switch back to "Compose" view to see the preview</li>
                <li>Publish your post</li>
            </ol>
        </div>
    </div>

    <script>
        // Dark mode detection
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            document.documentElement.classList.add('dark');
        }
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
            if (event.matches) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        });

        // DOM elements
        const urlInput = document.getElementById('urlInput');
        const widthInput = document.getElementById('widthInput');
        const heightInput = document.getElementById('heightInput');
        const borderInput = document.getElementById('borderInput');
        const allowFullscreen = document.getElementById('allowFullscreen');
        const responsiveFrame = document.getElementById('responsiveFrame');
        const generateBtn = document.getElementById('generateBtn');
        const outputSection = document.getElementById('outputSection');
        const previewSection = document.getElementById('previewSection');
        const embedCode = document.getElementById('embedCode');
        const copyBtn = document.getElementById('copyBtn');
        const copySuccess = document.getElementById('copySuccess');
        const previewContainer = document.getElementById('previewContainer');

        // Validation function
        function isValidUrl(string) {
            try {
                new URL(string);
                return true;
            } catch (_) {
                return false;
            }
        }

        // Generate iframe code
        function generateIframeCode() {
            const url = urlInput.value.trim();
            
            if (!url) {
                showAlert('Please enter a URL');
                return;
            }

            if (!isValidUrl(url)) {
                showAlert('Please enter a valid URL');
                return;
            }

            const width = widthInput.value.trim() || '100%';
            const height = heightInput.value.trim() || '400';
            const border = borderInput.value;
            const fullscreen = allowFullscreen.checked;
            const responsive = responsiveFrame.checked;

            let iframeAttributes = [];
            iframeAttributes.push(`src="${url}"`);
            iframeAttributes.push(`width="${width}"`);
            iframeAttributes.push(`height="${height}"`);
            iframeAttributes.push(`frameborder="${border}"`);
            
            if (fullscreen) {
                iframeAttributes.push('allowfullscreen');
            }

            let iframeCode = `<iframe ${iframeAttributes.join(' ')}></iframe>`;

            // Add responsive wrapper if requested
            if (responsive) {
                iframeCode = `<div style="position: relative; overflow: hidden; padding-top: 56.25%; /* 16:9 Aspect Ratio */">
    <iframe src="${url}" 
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: ${border}px solid #ccc;" 
            frameborder="${border}"${fullscreen ? ' allowfullscreen' : ''}>
    </iframe>
</div>`;
            }

            // Display the code
            embedCode.value = iframeCode;
            outputSection.classList.remove('hidden');

            // Update preview
            updatePreview(url, width, height, border, fullscreen, responsive);
        }

        // Update preview
        function updatePreview(url, width, height, border, fullscreen, responsive) {
            let previewIframe;
            
            if (responsive) {
                previewContainer.innerHTML = `
                    <div style="position: relative; overflow: hidden; padding-top: 56.25%;">
                        <iframe src="${url}" 
                                style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: ${border}px solid #ccc;" 
                                frameborder="${border}"${fullscreen ? ' allowfullscreen' : ''}>
                        </iframe>
                    </div>
                `;
            } else {
                const previewWidth = width.includes('%') ? '100%' : Math.min(parseInt(width) || 400, 600) + 'px';
                const previewHeight = Math.min(parseInt(height) || 400, 400) + 'px';
                
                previewContainer.innerHTML = `
                    <iframe src="${url}" 
                            width="${previewWidth}" 
                            height="${previewHeight}" 
                            frameborder="${border}"${fullscreen ? ' allowfullscreen' : ''}>
                    </iframe>
                `;
            }
            
            previewSection.classList.remove('hidden');
        }

        // Copy to clipboard
        async function copyToClipboard() {
            try {
                await navigator.clipboard.writeText(embedCode.value);
                copySuccess.classList.remove('hidden');
                setTimeout(() => {
                    copySuccess.classList.add('hidden');
                }, 3000);
            } catch (err) {
                // Fallback for older browsers
                embedCode.select();
                document.execCommand('copy');
                copySuccess.classList.remove('hidden');
                setTimeout(() => {
                    copySuccess.classList.add('hidden');
                }, 3000);
            }
        }

        // Custom alert function
        function showAlert(message) {
            const modal = document.createElement('div');
            modal.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            modal.innerHTML = `
                <div class="bg-white dark:bg-gray-800 p-6 rounded-lg shadow-lg max-w-sm w-full mx-4">
                    <p class="text-gray-700 dark:text-gray-300 mb-4">${message}</p>
                    <div class="flex justify-end">
                        <button class="px-4 py-2 bg-primary text-white hover:bg-primary-dark rounded" onclick="this.closest('.fixed').remove()">OK</button>
                    </div>
                </div>
            `;
            document.body.appendChild(modal);
        }

        // Event listeners
        generateBtn.addEventListener('click', generateIframeCode);
        copyBtn.addEventListener('click', copyToClipboard);
        
        // Generate on Enter key
        urlInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                generateIframeCode();
            }
        });

        // Auto-generate when inputs change (debounced)
        let debounceTimer;
        function debouncedGenerate() {
            clearTimeout(debounceTimer);
            debounceTimer = setTimeout(() => {
                if (urlInput.value.trim() && isValidUrl(urlInput.value.trim())) {
                    generateIframeCode();
                }
            }, 500);
        }

        [urlInput, widthInput, heightInput, borderInput, allowFullscreen, responsiveFrame].forEach(input => {
            input.addEventListener('input', debouncedGenerate);
            input.addEventListener('change', debouncedGenerate);
        });
    </script>
</body>
</html>



# Blogger Iframe Embed Generator

A modern, responsive iframe embed code generator for Blogger posts.  
Built with Tailwind CSS and supports dark mode, responsive frames, and live preview.
<p align="center">
  <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createatoolthatgeneratesiframeorcard-styleembedsforindividualbloggerpostscompletewiththumbnailtitleandreadmorebuttonforcross-blogpromotion754077096311972631.jpg" alt="Firebase Front-End Components Preview" width="600"/>
</p>

🔗 Live Demo: [https://beatzde4.blogspot.com/p/debeatzgh-floating-buttons-v1.html]

## 🚀 Features
- Dark mode support
- Fully responsive layout
- Live preview of the generated iframe
- Copy-to-clipboard functionality
- Customizable width, height, border, fullscreen, and responsiveness

## 📦 Usage
1. Enter the URL you want to embed.
2. Customize width, height, and border.
3. Toggle fullscreen and responsiveness.
4. Click "Generate" to preview and copy the iframe code.
5. Paste the code into Blogger's HTML editor.

## 🧪 Tech Stack
- HTML5
- JavaScript
- Tailwind CSS

## 💡 How to Embed in Blogger
1. Copy the generated iframe code.
2. Go to your Blogger post → "HTML" view.
3. Paste it where you want the iframe to appear.
4. Switch back to "Compose" to see the result.

---

© 2025 [Debeatzgh](https://beatzde4.blogspot.com)


# 🚀 DeBeatzGH – AI Tools & Side Hustle Hub  

![DeBeatzGH Thumbnail](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticdesignfeaturinganai-themedicon28likeabraincircuitorrobot29overlaidwithdebeatzghoraitoolshustles6089986211026037047.jpg)  

## 🌟 About  
Welcome to **[DeBeatzGH](https://debeatzgh.wordpress.com/)** — your go-to hub for **AI tools, side hustle strategies, blogging resources, and digital growth guides**.  

Our platform is built to help **students, creators, startups, and professionals** unlock the power of AI, monetize their skills, and thrive in today’s digital economy.  

### ✨ What You’ll Find  
- 💡 Explore **AI prompts, tools, and hacks**  
- 📈 Discover **side hustle strategies & online income ideas**  
- ✍️ Access **blogging & digital business guides**  
- 🚀 Stay ahead with **regular updates and fresh insights**  

---

## 👉 Get Started  
🔥 **Start your journey today → [Visit DeBeatzGH](https://debeatzgh.wordpress.com/)**  

---

<!-- README: DebeatzGH Digital Store (HTML-friendly for GitHub) -->
<div align="center">
  <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">
    <img
      src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"
      alt="DebeatzGH Digital Store"
      style="max-width:100%; border-radius:16px;"
    />
  </a>

  <h1 style="margin-top: 14px;">DebeatzGH Digital Store</h1>
  <p style="max-width:780px;">
    Your hub for AI insights, tech tutorials, side-hustle playbooks, and productivity tools.
    Learn, build, and launch digital projects faster.
  </p>

  <!-- CTAs -->
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      🚀 View Live App
    </a>
    <a href="https://github.com/debeatzgh1/Personal-Portfolio-site-" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #111827;">
      ⭐ Star this Repo
    </a>
  </p>
</div>

<hr/>

<h2>Overview</h2>
<p>
  <strong>DebeatzGH</strong> helps beginners and creators build profitable digital assets:
  blogs, affiliate funnels, AI-assisted content, and more. Explore tutorials, tools, and
  ready-to-use components to speed up your workflow.
</p>

<h2>Features</h2>
<ul>
  <li><strong>AI & Tech Learning:</strong> Bite-sized guides for modern tools and workflows.</li>
  <li><strong>Side-Hustle Playbooks:</strong> Practical steps to validate and launch ideas.</li>
  <li><strong>Productivity Toolkit:</strong> Reusable widgets, templates, and scripts.</li>
  <li><strong>Beginner-Friendly:</strong> Clear explanations, curated resources, and examples.</li>
</ul>

<h2>Quick Start</h2>
<ol>
  <li>Clone:
    <pre><code>git clone https://github.com/debeatzgh1/Personal-Portfolio-site-</code></pre>
  </li>
  <li>Enter folder:
    <pre><code>cd debeatzgh</code></pre>
  </li>
  <li>Install deps (adjust to your stack):
    <pre><code># Node
npm install
npm run dev

# or Python
pip install -r requirements.txt
python app.py</code></pre>
  </li>
  <li>Open in browser:
    <pre><code>http://localhost:3000</code></pre>
  </li>
</ol>

<h2>Project Links</h2>
<ul>
  <li>🌐 Live App: <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">socialcreator.com/debeatzgh</a></li>
  <li>🖼️ Thumbnail: <a href="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" target="_blank" rel="noopener">View image</a></li>
</ul>

<h2>Contributing</h2>
<p>
  Contributions are welcome! Open an issue for bugs or ideas. For changes, fork the repo,
  create a feature branch, and submit a pull request.
</p>

<h2>License</h2>
<p>
  Released under the <a href="./LICENSE">MIT License</a>.
</p>

<hr/>

<div align="center">
  <p><em>If this project helps you, consider giving it a star. It really helps! ⭐</em></p>
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin-top:6px; border-radius:10px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      Open DebeatzGH Now →
    </a>
  </p>
</div>
