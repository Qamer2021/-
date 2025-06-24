<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>هل تعلم؟ معلومات لا محدودة</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Import Inter font for a modern look */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');

        body {
            font-family: 'Inter', sans-serif;
            direction: rtl; /* Set default text direction to right-to-left */
            background-color: #f0f4f8; /* Light background */
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
            background-image: linear-gradient(to bottom right, #e0f2fe, #bbdefb); /* Subtle gradient */
            overflow-x: hidden; /* Prevent horizontal scroll */
        }

        /* Container for the main app content */
        .app-container {
            width: 100%;
            max-width: 600px;
            display: flex;
            flex-direction: column;
            align-items: center;
            flex-grow: 1; /* Allow content to grow */
            margin-top: 2rem; /* Space from header */
        }

        /* Fact display area styling */
        .fact-display {
            background-color: #e3f2fd; /* Lighter blue background */
            color: #1a202c; /* Dark text for contrast */
            padding: 2.5rem;
            border-radius: 1.5rem; /* More rounded corners */
            margin-bottom: 2rem;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem; /* Larger font size */
            font-weight: 500;
            line-height: 1.6;
            text-align: center;
            box-shadow: inset 0 3px 6px rgba(0, 0, 0, 0.1); /* Inner shadow */
            transition: all 0.4s ease-in-out; /* Smooth transitions */
            border: 1px solid #a7d3f8; /* Subtle border */
        }

        /* Animation for fact display */
        @keyframes factFadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .fact-display.animate {
            animation: factFadeIn 0.6s ease-out forwards;
        }

        /* Button styling */
        .generate-button {
            background-image: linear-gradient(to right, #4CAF50 0%, #388E3C 100%); /* Green gradient */
            color: white;
            padding: 1.25rem 2.5rem;
            border: none;
            border-radius: 9999px; /* Pill shape */
            font-size: 1.25rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2); /* Stronger shadow */
            position: relative;
            overflow: hidden;
            letter-spacing: 0.5px;
            text-transform: uppercase; /* Uppercase text */
        }
        .generate-button:hover {
            transform: translateY(-5px); /* Lift on hover */
            box-shadow: 0 15px 25px rgba(0, 0, 0, 0.3);
        }
        .generate-button:active {
            transform: translateY(0);
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
        }
        /* Ripple effect on button click */
        .generate-button::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 300%;
            height: 300%;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 50%;
            transform: translate(-50%, -50%) scale(0);
            transition: transform 0.5s ease;
            z-index: 0;
        }
        .generate-button:hover::before {
            transform: translate(-50%, -50%) scale(1);
        }
        .generate-button span {
            position: relative;
            z-index: 1;
        }
        .generate-button:disabled {
            background-image: linear-gradient(to right, #a5d6a7 0%, #81c784 100%);
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        /* Header styling */
        header {
            width: 100%;
            max-width: 600px;
            background-color: #fff;
            padding: 1rem 1.5rem;
            border-radius: 0.75rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative; /* For dropdown positioning */
            z-index: 20; /* Ensure header is above other content */
        }

        /* Menu button in header */
        .menu-button {
            padding: 0.5rem;
            border-radius: 9999px;
            color: #1e88e5; /* Blue color for icon */
            transition: background-color 0.2s;
        }
        .menu-button:hover {
            background-color: #e3f2fd; /* Light blue hover */
        }

        /* Dropdown menu styling */
        .dropdown-menu {
            position: absolute;
            top: 100%; /* Position below header */
            right: 0;
            margin-top: 0.5rem;
            width: 12rem;
            background-color: #fff;
            border-radius: 0.5rem;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
            padding: 0.5rem 0;
            opacity: 0;
            transform: translateY(-10px);
            visibility: hidden;
            transition: opacity 0.3s ease-out, transform 0.3s ease-out, visibility 0.3s;
            z-index: 30; /* Ensure dropdown is above header */
        }
        .dropdown-menu.open {
            opacity: 1;
            transform: translateY(0);
            visibility: visible;
        }
        .dropdown-menu button {
            display: flex;
            align-items: center;
            width: 100%;
            padding: 0.75rem 1rem;
            text-align: right;
            color: #333;
            font-size: 1rem;
            background: none;
            border: none;
            cursor: pointer;
            transition: background-color 0.2s, color 0.2s;
        }
        .dropdown-menu button:hover {
            background-color: #e3f2fd;
            color: #1e88e5;
        }
        .dropdown-menu button svg {
            margin-left: 0.75rem; /* Space between icon and text */
            color: #1e88e5; /* Icon color */
        }

        /* Modal styling */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7); /* Darker overlay */
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease-out, visibility 0.3s;
            z-index: 50; /* Ensure modal is on top */
        }
        .modal-overlay.open {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background-color: #fff;
            padding: 2rem;
            border-radius: 1rem;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3); /* Stronger shadow */
            max-width: 500px;
            width: 90%;
            transform: scale(0.95);
            transition: transform 0.3s ease-out;
        }
        .modal-overlay.open .modal-content {
            transform: scale(1);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid #e0e0e0;
        }
        .modal-header h2 {
            font-size: 1.75rem;
            font-weight: bold;
            color: #333;
        }
        .modal-close-button {
            padding: 0.5rem;
            border-radius: 9999px;
            color: #757575;
            transition: background-color 0.2s;
        }
        .modal-close-button:hover {
            background-color: #f5f5f5;
        }
        .modal-body p {
            margin-bottom: 1rem;
            color: #555;
            line-height: 1.6;
        }
        .modal-body p:last-child {
            margin-bottom: 0;
        }

        /* Responsive adjustments */
        @media (max-width: 640px) {
            .app-container {
                padding: 0 10px;
            }
            .fact-display {
                font-size: 1.25rem;
                padding: 2rem;
            }
            .generate-button {
                font-size: 1.1rem;
                padding: 1rem 2rem;
            }
            header {
                padding: 0.75rem 1rem;
            }
            .modal-content {
                padding: 1.5rem;
                width: 95%;
            }
            .modal-header h2 {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>

    <!-- Header Section -->
    <header>
        <h1 class="text-2xl font-extrabold text-blue-700">هل تعلم؟</h1>
        <button id="menuButton" class="menu-button">
            <!-- Menu Icon (Hamburger) -->
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-menu">
                <line x1="4" x2="20" y1="12" y2="12"></line>
                <line x1="4" x2="20" y1="6" y2="6"></line>
                <line x1="4" x2="20" y1="18" y2="18"></line>
            </svg>
        </button>

        <!-- Dropdown Menu -->
        <div id="dropdownMenu" class="dropdown-menu">
            <button id="privacyPolicyBtn" class="flex items-center">
                <!-- Shield Icon -->
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-shield">
                    <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                </svg>
                <span>سياسة الخصوصية</span>
            </button>
            <button id="aboutAppBtn" class="flex items-center">
                <!-- Info Icon -->
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-info">
                    <circle cx="12" cy="12" r="10"></circle>
                    <path d="M12 16v-4"></path>
                    <path d="M12 8h.01"></path>
                </svg>
                <span>حول التطبيق</span>
            </button>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="app-container">
        <div id="factDisplay" class="fact-display">
            جاري تحميل أول معلومة...
        </div>
        <button id="generateFactBtn" class="generate-button">
            <span>اكتشف معلومة جديدة!</span>
        </button>
    </main>

    <!-- Privacy Policy Modal -->
    <div id="privacyModal" class="modal-overlay">
        <div class="modal-content">
            <div class="modal-header">
                <h2>سياسة الخصوصية</h2>
                <button class="modal-close-button" data-close-modal="privacy">
                    <!-- Close Icon (X) -->
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-x">
                        <path d="M18 6 6 18"></path>
                        <path d="m6 6 12 12"></path>
                    </svg>
                </button>
            </div>
            <div class="modal-body">
                <p>
                    نحن نأخذ خصوصيتك على محمل الجد. هذا التطبيق لا يجمع أي معلومات شخصية منك. جميع المعلومات المعروضة يتم إنشاؤها عشوائياً بواسطة نموذج الذكاء الاصطناعي ولا يتم تخزينها أو مشاركتها.
                </p>
                <p>
                    نحن نستخدم اتصالك بالإنترنت فقط لجلب معلومات جديدة من نموذج الذكاء الاصطناعي. لا يتم حفظ سجلات استخدامك أو معلومات جهازك.
                </p>
                <p>
                    باستخدام هذا التطبيق، فإنك توافق على سياسة الخصوصية هذه. إذا كان لديك أي أسئلة، فلا تتردد في الاتصال بنا.
                </p>
            </div>
        </div>
    </div>

    <!-- About App Modal -->
    <div id="aboutModal" class="modal-overlay">
        <div class="modal-content">
            <div class="modal-header">
                <h2>حول التطبيق</h2>
                <button class="modal-close-button" data-close-modal="about">
                    <!-- Close Icon (X) -->
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-x">
                        <path d="M18 6 6 18"></path>
                        <path d="m6 6 12 12"></path>
                    </svg>
                </button>
            </div>
            <div class="modal-body">
                <p>
                    تطبيق "هل تعلم؟" هو تطبيق بسيط وممتع يهدف إلى تزويدك بمعلومات عامة عشوائية بلمسة زر واحدة.
                </p>
                <p>
                    يتم إنشاء المعلومات المعروضة بواسطة نموذج ذكاء اصطناعي لضمان وجود عدد لا نهائي من الحقائق الجديدة والمثيرة للاهتمام.
                </p>
                <p>
                    نتمنى أن تستمتع باكتشاف معلومات جديدة كل يوم!
                    <br/>
                    <span class="font-semibold">الإصدار: 1.0</span>
                </p>
            </div>
        </div>
    </div>

    <script>
        const factDisplay = document.getElementById('factDisplay');
        const generateFactBtn = document.getElementById('generateFactBtn');
        const menuButton = document.getElementById('menuButton');
        const dropdownMenu = document.getElementById('dropdownMenu');
        const privacyPolicyBtn = document.getElementById('privacyPolicyBtn');
        const aboutAppBtn = document.getElementById('aboutAppBtn');
        const privacyModal = document.getElementById('privacyModal');
        const aboutModal = document.getElementById('aboutModal');

        // Function to show a modal
        function showModal(modalElement) {
            modalElement.classList.add('open');
        }

        // Function to hide a modal
        function hideModal(modalElement) {
            modalElement.classList.remove('open');
        }

        // --- Fact Generation Logic ---
        async function fetchNewFact() {
            generateFactBtn.disabled = true; // Disable button during loading
            factDisplay.textContent = "جاري تحميل معلومة جديدة..."; // Loading message
            factDisplay.classList.remove('animate'); // Remove previous animation class

            try {
                // Prepare the payload for the Gemini API
                let chatHistory = [];
                chatHistory.push({
                    role: "user",
                    parts: [{ text: "أعطني معلومة عامة عشوائية في صيغة 'هل تعلم أن...' باللغة العربية. اجعلها معلومة واحدة ومختصرة." }]
                });

                const payload = { contents: chatHistory };
                const apiKey = ""; // Canvas will provide this key at runtime
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }

                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    factDisplay.textContent = text.trim();
                } else {
                    factDisplay.textContent = "عذرًا، لم أتمكن من جلب معلومة جديدة. الرجاء المحاولة مرة أخرى.";
                    console.error("Unexpected LLM response structure:", result);
                }
            } catch (error) {
                console.error("Error fetching fact:", error);
                factDisplay.textContent = "حدث خطأ أثناء جلب المعلومة. يرجى التحقق من اتصالك بالإنترنت.";
            } finally {
                // Re-add animation class after content is loaded
                void factDisplay.offsetWidth; // Trigger reflow
                factDisplay.classList.add('animate');
                generateFactBtn.disabled = false; // Re-enable button
            }
        }

        // --- Event Listeners ---

        // Generate Fact Button
        generateFactBtn.addEventListener('click', fetchNewFact);

        // Menu Button (Toggle Dropdown)
        menuButton.addEventListener('click', (event) => {
            dropdownMenu.classList.toggle('open');
            event.stopPropagation(); // Prevent immediate closing from document click
        });

        // Close dropdown when clicking outside
        document.addEventListener('click', (event) => {
            if (!dropdownMenu.contains(event.target) && !menuButton.contains(event.target)) {
                dropdownMenu.classList.remove('open');
            }
        });

        // Privacy Policy Button in Dropdown
        privacyPolicyBtn.addEventListener('click', () => {
            hideModal(dropdownMenu); // Close dropdown first
            showModal(privacyModal);
        });

        // About App Button in Dropdown
        aboutAppBtn.addEventListener('click', () => {
            hideModal(dropdownMenu); // Close dropdown first
            showModal(aboutModal);
        });

        // Close Modals (using event delegation for all close buttons and overlay)
        document.querySelectorAll('.modal-close-button').forEach(button => {
            button.addEventListener('click', (event) => {
                const modalId = event.currentTarget.dataset.closeModal;
                if (modalId === 'privacy') hideModal(privacyModal);
                else if (modalId === 'about') hideModal(aboutModal);
            });
        });

        // Close modal when clicking outside of modal content
        privacyModal.addEventListener('click', (event) => {
            if (event.target === privacyModal) { // Check if clicked directly on overlay
                hideModal(privacyModal);
            }
        });
        aboutModal.addEventListener('click', (event) => {
            if (event.target === aboutModal) { // Check if clicked directly on overlay
                hideModal(aboutModal);
            }
        });

        // Initial fact fetch on page load
        window.onload = fetchNewFact;
    </script>
</body>
</html>
