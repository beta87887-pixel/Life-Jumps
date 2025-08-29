# Life-Jumps
Live multiple lives, make bold choices, and see where destiny takes you! 🌟 From careers and love to fortune and fame, every decision shapes your journey. Risk it, chase dreams, and experience a dynamic world that reacts to you. 🚀 Life Jumps—take the leap, live without limits!
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Life Jumps</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Define CSS Variables for easy theme management (Dark Mode by default) */
        :root {
            --primary-bg: #1a1a2e;
            --secondary-bg: #16213e;
            --card-bg: #0f3460;
            --text-color: #e0e0e0;
            --accent-color: #e94560;
            --button-color: #533483;
            --button-hover: #452a6b;
            --border-color: #0f3460;
            --shadow-color: rgba(0, 0, 0, 0.4);
            --good-stat: #28a745;
            --neutral-stat: #ffc107;
            --bad-stat: #dc3545;
        }

        /* Light Mode Variables */
        body.light-mode {
            --primary-bg: #f0f2f5;
            --secondary-bg: #ffffff;
            --card-bg: #e0e6ed;
            --text-color: #333333;
            --accent-color: #1a73e8; /* A brighter accent for light mode */
            --button-color: #4285f4;
            --button-hover: #357ae8;
            --border-color: #c5ced7;
            --shadow-color: rgba(0, 0, 0, 0.1);
            --good-stat: #28a745;
            --neutral-stat: #fd7e14; /* Slightly different neutral for visibility */
            --bad-stat: #dc3545;
        }

        body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--primary-bg);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: auto; /* Allow scrolling for content that exceeds viewport height */
            box-sizing: border-box;
            transition: background-color 0.3s ease, color 0.3s ease; /* Smooth transition for theme change */
        }

        .game-container {
            background-color: var(--secondary-bg);
            border-radius: 15px;
            box-shadow: 0 10px 30px var(--shadow-color);
            padding: 2.5rem;
            width: 90%;
            max-width: 600px;
            text-align: center;
            border: 2px solid var(--border-color);
            margin: 20px 0; /* Add vertical margin for better spacing on small screens */
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            transition: background-color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
            position: relative; /* For positioning the theme toggle */
        }

        h1 {
            color: var(--accent-color);
            font-size: 2.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 5px var(--shadow-color);
        }

        .stats-panel, .age-panel {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 1rem;
            box-shadow: 0 4px 10px var(--shadow-color);
            border: 1px solid var(--border-color);
            transition: background-color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 0.8rem;
        }

        .stat-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 1.1rem;
            font-weight: 600;
            padding: 0.5rem 0.8rem;
            border-radius: 8px;
            background-color: var(--primary-bg);
            color: var(--text-color);
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        .stat-value {
            font-weight: 700;
            margin-left: 0.5rem;
            padding: 0.2em 0.5em;
            border-radius: 5px;
        }

        .stat-value.good { background-color: var(--good-stat); color: white; }
        .stat-value.neutral { background-color: var(--neutral-stat); color: var(--primary-bg); }
        .stat-value.bad { background-color: var(--bad-stat); color: white; }

        .age-panel p {
            font-size: 1.3rem;
            font-weight: 600;
            margin: 0;
            color: var(--accent-color);
            transition: color 0.3s ease;
        }

        .event-panel {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 10px var(--shadow-color);
            border: 1px solid var(--border-color);
            transition: background-color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
        }

        .event-description {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
            line-height: 1.5;
        }

        .choices-grid {
            display: grid;
            gap: 1rem;
        }

        .choice-button {
            background-color: var(--button-color);
            color: var(--text-color);
            border: none;
            padding: 1rem 1.5rem;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
            box-shadow: 0 3px 8px var(--shadow-color);
        }

        .choice-button:hover:not(:disabled) {
            background-color: var(--button-hover);
            transform: translateY(-3px);
            box-shadow: 0 6px 15px var(--shadow-color);
        }

        .choice-button:active:not(:disabled) {
            transform: translateY(0);
            box-shadow: 0 2px 5px var(--shadow-color);
        }

        .choice-button:disabled {
            background-color: #4a4a4a;
            cursor: not-allowed;
            opacity: 0.7;
        }

        .message-box {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 1.5rem;
            margin-top: 1.5rem;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 10px var(--shadow-color);
            color: var(--text-color);
            transition: background-color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease, color 0.3s ease;
        }

        .message-box h3 {
            color: var(--accent-color);
            margin-top: 0;
            font-size: 1.8rem;
            transition: color 0.3s ease;
        }

        .message-box p {
            font-size: 1.1rem;
            margin-bottom: 1rem;
        }

        .restart-button {
            background-color: var(--accent-color);
            color: var(--text-color);
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 3px 8px var(--shadow-color);
            margin-top: 1rem;
        }

        .restart-button:hover {
            background-color: #c2314a;
            transform: translateY(-2px);
        }

        .theme-toggle-button {
            position: absolute;
            top: 15px;
            right: 15px;
            background-color: var(--button-color);
            color: var(--text-color);
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.2rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 5px var(--shadow-color);
            transition: background-color 0.3s ease, color 0.3s ease, transform 0.2s ease;
            z-index: 10;
        }

        .theme-toggle-button:hover {
            background-color: var(--button-hover);
            transform: scale(1.05);
        }

        /* Responsive adjustments */
        @media (max-width: 600px) {
            .game-container {
                padding: 1.5rem;
                gap: 1rem;
            }
            h1 {
                font-size: 2rem;
            }
            .stats-grid {
                grid-template-columns: 1fr; /* Stack stats on smaller screens */
            }
            .event-description {
                font-size: 1rem;
            }
            .choice-button {
                font-size: 1rem;
                padding: 0.8rem 1rem;
            }
            .theme-toggle-button {
                top: 10px;
                right: 10px;
                width: 35px;
                height: 35px;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <button id="theme-toggle" class="theme-toggle-button">
            <!-- Initial icon will be set by JS based on current theme -->
        </button>

        <h1>Life Jumps</h1>

        <!-- Player Stats Panel -->
        <div class="stats-panel">
            <div class="stats-grid">
                <div class="stat-item">Health: <span id="stat-health" class="stat-value"></span></div>
                <div class="stat-item">Happiness: <span id="stat-happiness" class="stat-value"></span></div>
                <div class="stat-item">Smarts: <span id="stat-smarts" class="stat-value"></span></div>
                <div class="stat-item">Money: <span id="stat-money" class="stat-value"></span></div>
                <div class="stat-item">Car: <span id="stat-car" class="stat-value"></span></div>
                <div class="stat-item">House: <span id="stat-house" class="stat-value"></span></div>
                <div class="stat-item">Spouse: <span id="stat-spouse" class="stat-value"></span></div>
                <div class="stat-item">Children: <span id="stat-children" class="stat-value"></span></div>
                <div class="stat-item">Country: <span id="stat-country" class="stat-value"></span></div>
                <div class="stat-item">Social Followers: <span id="stat-social-followers" class="stat-value"></span></div>
                <div class="stat-item">Major: <span id="stat-major" class="stat-value"></span></div>
            </div>
        </div>

        <!-- Age Panel -->
        <div class="age-panel">
            <p>Age: <span id="current-age">0</span></p>
        </div>

        <!-- Event Panel -->
        <div class="event-panel" id="event-panel">
            <p class="event-description" id="event-description">Welcome to Life Jumps! Click 'Start New Life' to begin your journey.</p>
            <div class="choices-grid" id="choices-grid">
                <button class="choice-button" id="start-button">Start New Life</button>
            </div>
        </div>

        <!-- Message Box for Game Over or Special Messages -->
        <div class="message-box" id="message-box" style="display:none;">
            <h3 id="message-title"></h3>
            <p id="message-content"></p>
            <button class="restart-button" id="restart-game-button" style="display:none;">Restart Game</button>
        </div>
    </div>

    <script>
        // --- Game State Variables ---
        let player = {}; // Object to hold player's stats
        let currentAge = 0; // Current age of the player
        let gameOver = false; // Flag to indicate if the game has ended
        const MALE_NAMES = ['Liam', 'Noah', 'Oliver', 'James', 'Lucas', 'Benjamin', 'Elijah'];
        const FEMALE_NAMES = ['Olivia', 'Emma', 'Ava', 'Sophia', 'Isabella', 'Mia', 'Charlotte'];

        // --- DOM Elements ---
        const body = document.body;
        const statHealth = document.getElementById('stat-health');
        const statHappiness = document.getElementById('stat-happiness');
        const statSmarts = document.getElementById('stat-smarts');
        const statMoney = document.getElementById('stat-money');
        const statCar = document.getElementById('stat-car');
        const statHouse = document.getElementById('stat-house');
        const statSpouse = document.getElementById('stat-spouse');
        const statChildren = document.getElementById('stat-children');
        const statCountry = document.getElementById('stat-country'); // New stat
        const statSocialFollowers = document.getElementById('stat-social-followers'); // New stat
        const statMajor = document.getElementById('stat-major'); // New stat
        const currentAgeSpan = document.getElementById('current-age');
        const eventDescription = document.getElementById('event-description');
        const choicesGrid = document.getElementById('choices-grid');
        const startButton = document.getElementById('start-button');
        const messageBox = document.getElementById('message-box');
        const messageTitle = document.getElementById('message-title');
        const messageContent = document.getElementById('message-content');
        const restartGameButton = document.getElementById('restart-game-button');
        const themeToggle = document.getElementById('theme-toggle');

        // --- Game Configuration ---
        const MAX_AGE = 100; // Maximum age a player can reach naturally
        const STAT_THRESHOLD_GOOD = 70; // Stat value for 'good' color
        const STAT_THRESHOLD_BAD = 30;  // Stat value for 'bad' color

        const COUNTRIES = ['USA', 'Canada', 'UK', 'Germany', 'Australia', 'Japan', 'Brazil'];

        // --- Theme Management ---
        let isLightMode = false; // Default to dark mode

        /**
         * Applies the theme based on the isLightMode variable.
         * Stores the preference in local storage.
         */
        function applyTheme() {
            if (isLightMode) {
                body.classList.add('light-mode');
                themeToggle.textContent = '🌙'; // Moon icon for light mode
            } else {
                body.classList.remove('light-mode');
                themeToggle.textContent = '☀️'; // Sun icon for dark mode
            }
            localStorage.setItem('lifeJumpsTheme', isLightMode ? 'light' : 'dark');
        }

        /**
         * Toggles the theme between light and dark mode.
         */
        function toggleTheme() {
            isLightMode = !isLightMode;
            applyTheme();
        }

        // --- Event Definitions ---
        // Events are categorized by age range. Each event has a description and choices.
        // Choices have text, stat effects, and potentially a 'nextAgeJump' to quickly advance years.
        const gameEvents = {
            0: [ // Birth
                {
                    description: "You've just been born! Your life is a blank canvas.",
                    choices: [
                        { text: "Begin your journey!", effect: {}, nextAgeJump: 6 } // Jump to childhood
                    ]
                }
            ],
            6: [ // Childhood (6-12 years)
                {
                    description: "It's your first day of school. How do you approach it?",
                    choices: [
                        { text: "Try to make friends with everyone.", effect: { happiness: 10, smarts: 5 } },
                        { text: "Focus on your studies diligently.", effect: { smarts: 15, happiness: -5 } },
                        { text: "Find the other kids and play together!", effect: { happiness: 15, health: 5 } } // Adjusted for age-appropriateness
                    ]
                },
                {
                    description: "A classmate is struggling with a school project. What do you do?",
                    choices: [
                        { text: "Offer to help them.", effect: { happiness: 10, smarts: 5 } },
                        { text: "Focus on your own project.", effect: { smarts: 5 } },
                        { text: "Play a small prank on them (gently!).", effect: { happiness: 5, smarts: -5 }, condition: () => Math.random() < 0.5 } // 50% chance of playful mischief
                    ]
                },
                {
                    description: "You found some money on the ground. What do you do?",
                    choices: [
                        { text: "Look for its owner.", effect: { happiness: 10, money: 100 } }, // Good karma, maybe a small reward
                        { text: "Keep it for yourself.", effect: { money: 200, happiness: -5 } },
                        { text: "Buy candy for everyone!", effect: { happiness: 15, money: -50 } }
                    ]
                },
                {
                    description: "Your school is starting a new sports club. Do you join?",
                    choices: [
                        { text: "Yes, to be active and have fun!", effect: { health: 15, happiness: 10 } },
                        { text: "No, prefer reading and quiet activities.", effect: { smarts: 10, happiness: 5 } }
                    ]
                }
            ],
            13: [ // Teen Years (13-17 years)
                // New event for age 17 university decision
                {
                    description: "You're turning 17 soon! High school is almost over. What are your plans after graduation?",
                    choices: [
                        { text: "Go to university to get a degree!", effect: { smarts: 5, happiness: 5 }, nextEvent: 'university_payment_options', condition: () => currentAge === 17 },
                        { text: "Start working and save money.", effect: { money: 1000, happiness: 10 }, condition: () => currentAge === 17, nextAgeJump: 18 }
                    ],
                    condition: () => currentAge === 17 // This event specifically triggers at age 17
                },
                {
                    description: "You're starting high school. What's your focus?",
                    choices: [
                        { text: "Academics and grades.", effect: { smarts: 20, happiness: -5 } },
                        { text: "Social life and making new friends.", effect: { happiness: 15, smarts: -5 } },
                        { text: "Sports and extracurriculars.", effect: { health: 10, happiness: 5 } }
                    ]
                },
                {
                    description: "Your friends invite you to a fun gathering. Your parents aren't sure. What's your choice?",
                    choices: [
                        { text: "Ask politely and explain why you want to go.", effect: { happiness: 10, smarts: 5 } },
                        { text: "Stay home and respect your parents' wishes.", effect: { happiness: 5, smarts: 5 } },
                        { text: "Try to convince them, offering to do extra chores.", effect: { happiness: 5, smarts: 5, money: -20 } } // lose a bit of pocket money
                    ]
                },
                {
                    description: "A chance to get a part-time job comes up. Do you take it?",
                    choices: [
                        { text: "Yes, to earn some money for fun things!", effect: { money: 300, happiness: 5, smarts: -5 } },
                        { text: "No, focus on school and free time.", effect: { happiness: 10, smarts: 5 } }
                    ]
                },
                {
                    description: "You meet someone new at school who seems special. How do you proceed?",
                    choices: [
                        { text: "Talk to them and try to become friends.", effect: { happiness: 15, smarts: -5 } },
                        { text: "Become good friends first, see where it goes.", effect: { happiness: 10, smarts: 5 } },
                        { text: "Shy away, it's too nerve-wracking.", effect: { happiness: -10 } }
                    ]
                },
                // New event for mischievous activity (instead of "commit a crime")
                {
                    description: "A friend dares you to do something mischievous at school (e.g., drawing on the board).",
                    choices: [
                        {
                            text: "Go for it, it's just a bit of fun!",
                            effect: { happiness: 10, smarts: -10, money: -50 }, // Small negative consequences
                            condition: () => Math.random() < 0.7 // 70% chance of minor negative outcome (getting caught/minor fine)
                        },
                        { text: "Decline, it's better to follow the rules.", effect: { happiness: 5, smarts: 5 } }
                    ]
                },
                {
                    description: "You want to try out for the school sports team! ⚽🏀",
                    choices: [
                        { text: "Dedicate yourself to practice.", effect: { health: 20, happiness: 15, smarts: 5 } },
                        { text: "Just try out, no extra effort.", effect: { health: 5, happiness: 5 } }
                    ]
                },
                {
                    description: "You're thinking about creating a social media profile. What's your approach?",
                    choices: [
                        { text: "Post regularly, share interests.", effect: { happiness: 10, socialFollowers: 100 } },
                        { text: "Keep it private, connect with close friends only.", effect: { happiness: 5 } },
                        { text: "Stay offline, focus on real-life interactions.", effect: { smarts: 5, happiness: 5 } }
                    ]
                }
            ],
            18: [ // Young Adult (18-29 years)
                // New, more general spouse event if not married
                {
                    description: "You're feeling ready for a serious relationship. Do you want to find a partner?",
                    choices: [
                        { text: "Yes, look for a spouse!", effect: { happiness: 15 }, nextEvent: 'find_spouse', condition: () => !player.isMarried },
                        { text: "Not right now, focus on other things.", effect: { happiness: 5 }, nextAgeJump: 19, condition: () => !player.isMarried }
                    ],
                    condition: () => !player.isMarried && currentAge < 30 // Make this available until married or after 30
                },
                {
                    description: "You've finished high school. What's next?",
                    choices: [
                        { text: "Go to university to further your education.", effect: { smarts: 25, happiness: 5 }, nextEvent: 'university_payment_options' }, // Leads to special event
                        { text: "Start working full-time and save up.", effect: { money: 15000, smarts: -5 } },
                        { text: "Explore the world and gain new experiences.", effect: { happiness: 20, money: -5000, health: 5 } }
                    ],
                    condition: () => player.major === 'None' // Only ask if they haven't chosen a major through the age 17 event
                },
                {
                    description: "You're looking for your first car. What kind do you aim for?",
                    choices: [
                        { text: "A reliable, used car. (Cost: $5,000)", effect: { money: -5000, happiness: 10, hasCar: true }, condition: () => player.money >= 5000 && !player.hasCar },
                        { text: "A brand new, shiny car! (Cost: $20,000)", effect: { money: -20000, happiness: 20, hasCar: true }, condition: () => player.money >= 20000 && !player.hasCar },
                        { text: "Save money, use public transport.", effect: { money: 500, happiness: 5 }, condition: () => !player.hasCar }
                    ]
                },
                // Existing marriage proposal event, with refined conditions
                {
                    description: "You've been dating someone special and are thinking about taking the next step.",
                    choices: [
                        { text: "Propose marriage!💍", effect: { happiness: 30, money: -2000, isMarried: true }, condition: () => !player.isMarried && player.happiness >= 50 && currentAge >= 20 },
                        { text: "Continue dating and enjoying your time together.", effect: { happiness: 15 } }
                    ],
                    condition: () => !player.isMarried // Only show if not married
                },
                {
                    description: "Your health isn't what it used to be. What do you do?",
                    choices: [
                        { text: "Start exercising regularly and eat healthy.", effect: { health: 15, money: -500 } },
                        { text: "Keep your current habits, you're fine!", effect: { health: -10, happiness: 5 } }
                    ]
                },
                {
                    description: "A big sports competition is coming up. Do you try to join?",
                    choices: [
                        { text: "Train hard for the competition!", effect: { health: 25, happiness: 20, money: -1000 }, condition: () => player.health >= 40 },
                        { text: "Cheer from the sidelines!", effect: { happiness: 10 } }
                    ]
                },
                {
                    description: "Your social media account is growing! How do you handle it?",
                    choices: [
                        { text: "Post exciting content and engage with followers.", effect: { happiness: 15, socialFollowers: 500, smarts: -5 } },
                        { text: "Keep it casual, share with friends.", effect: { happiness: 5 } },
                        { text: "Take a break from social media.", effect: { happiness: 10, health: 5 } }
                    ]
                },
                {
                    description: "You're considering a big move to a new country! ✈️",
                    choices: COUNTRIES.map(country => ({
                        text: `Move to ${country}. (Cost: $10,000)`,
                        effect: { money: -10000, happiness: 20, country: country },
                        condition: () => player.money >= 10000 && player.country !== country
                    })).concat([
                        { text: "Stay in your current country.", effect: { happiness: 5 } }
                    ])
                },
            ],
            30: [ // Adult (30-59 years)
                {
                    description: "You're thinking about buying a home.",
                    choices: [
                        { text: "Buy a cozy starter home. (Cost: $100,000)", effect: { money: -100000, happiness: 25, hasHouse: true }, condition: () => player.money >= 100000 && !player.hasHouse },
                        { text: "Save more for a dream house. (Cost: $250,000)", effect: { money: -250000, happiness: 35, hasHouse: true }, condition: () => player.money >= 250000 && !player.hasHouse },
                        { text: "Continue renting, it's more flexible.", effect: { money: 10000, happiness: 5 }, condition: () => !player.hasHouse }
                    ]
                },
                // Children event, now leads to naming - this should appear regularly
                {
                    description: "You and your spouse are ready to expand your family! 👨‍👩‍👧‍👦",
                    choices: [
                        { text: "Have a child!", effect: { happiness: 40, money: -30000 }, nextEvent: 'child_birth', condition: () => player.isMarried && currentAge < 45 } // Leads to special event, limit age for having children
                    ],
                    condition: () => player.isMarried && player.children.length < 6 && currentAge >= 25 // Limit to 6 children
                },
                {
                    description: "A major financial investment opportunity arises. It's risky but could pay off big.",
                    choices: [
                        { text: "Invest heavily! 💰", effect: { money: 50000 }, chance: 0.5 }, // 50% chance to win big
                        { text: "Play it safe, invest cautiously.", effect: { money: 5000 } },
                        { text: "Don't invest at all, prefer security.", effect: {} }
                    ]
                },
                {
                    description: "You're feeling stressed at work. What's your coping mechanism?",
                    choices: [
                        { text: "Take a vacation and relax.", effect: { happiness: 15, money: -3000 } },
                        { text: "Work harder to overcome the challenges.", effect: { smarts: 10, health: -10 } },
                        { text: "Find a new hobby or activity to unwind.", effect: { happiness: 10, health: 5 } }
                    ]
                },
                {
                    description: "An old friend reaches out after years. What do you do?",
                    choices: [
                        { text: "Reconnect with them and catch up.", effect: { happiness: 10 } },
                        { text: "Politely decline, you're too busy.", effect: {} }
                    ]
                },
                {
                    description: "You have a chance to take part in a community sports event! 🏃‍♀️",
                    choices: [
                        { text: "Join the team and compete!", effect: { health: 15, happiness: 15, money: -200 } },
                        { text: "Support from the stands.", effect: { happiness: 5 } }
                    ]
                },
                {
                    description: "You're thinking about changing your social media presence. How do you evolve?",
                    choices: [
                        { text: "Become an influencer, create content.", effect: { happiness: 20, socialFollowers: 1000, money: 5000, smarts: -10 }, condition: () => player.socialFollowers >= 500 },
                        { text: "Use it to connect with family and old friends.", effect: { happiness: 10 } },
                        { text: "Delete your accounts, digital detox.", effect: { happiness: 15, health: 5 } }
                    ]
                },
                {
                    description: "A new job opportunity opens up in a different country! 🌍",
                    choices: COUNTRIES.map(country => ({
                        text: `Relocate to ${country}. (Cost: $20,000)`,
                        effect: { money: -20000, happiness: 25, country: country },
                        condition: () => player.money >= 20000 && player.country !== country
                    })).concat([
                        { text: "Stay in your current country.", effect: { happiness: 5 } }
                    ])
                },
            ],
            60: [ // Senior (60+ years)
                {
                    description: "You're approaching retirement. How do you plan to spend it?",
                    choices: [
                        { text: "Travel the world and see new places.", effect: { happiness: 20, money: -10000, health: 5 } },
                        { text: "Relax and enjoy hobbies at home with family.", effect: { happiness: 15, health: 10 } },
                        { text: "Stay active and volunteer in your community.", effect: { happiness: 25, health: 10 } }
                    ]
                },
                {
                    description: "Your health is declining. Do you seek medical attention?",
                    choices: [
                        { text: "Yes, visit a doctor regularly.", effect: { health: 15, money: -5000 } },
                        { text: "No, let nature take its course.", effect: { health: -20, happiness: -10 } }
                    ]
                },
                {
                    description: "You have an opportunity to pass on your wisdom to the next generation.",
                    choices: [
                        { text: "Mentor younger generations and share your experiences.", effect: { happiness: 15, smarts: 5 } },
                        { text: "Write your memoirs and leave a legacy.", effect: { happiness: 10, smarts: 10, money: 2000 } }
                    ]
                }
            ]
        };

        // --- Special Events (e.g., University Flow, Child Naming Flow) ---
        const specialEvents = {
            'university_payment_options': {
                description: "You've chosen to go to university! How will you pay for your education?",
                choices: [
                    { text: "Take out a student loan. (Debt: -$50,000)", effect: { money: -50000, smarts: 20, happiness: -5 }, nextEvent: 'choose_major' },
                    { text: "Apply for a scholarship. (Free money, high smarts needed!)", effect: { money: 0, smarts: 25, happiness: 10 }, condition: () => player.smarts >= 70, nextEvent: 'choose_major' },
                    { text: "Ask your parents to pay. (Cost: $20,000)", effect: { money: -20000, smarts: 15, happiness: 10 }, condition: () => player.money >= 20000, nextEvent: 'choose_major' } // Represents parental support
                ]
            },
            'choose_major': {
                description: "What major will you study?",
                choices: [
                    { text: "Computer Science (+30 Smarts, challenging)", effect: { smarts: 30, happiness: -5, major: 'Computer Science' } },
                    { text: "Psychology (+20 Happiness, understanding)", effect: { happiness: 20, smarts: 10, major: 'Psychology' } },
                    { text: "Health Sciences (+25 Health focus, caring)", effect: { health: 10, smarts: 25, happiness: 5, major: 'Health Sciences' } },
                    { text: "Business Administration (+25 Money potential, strategic)", effect: { money: 5000, smarts: 15, major: 'Business Administration' } },
                    { text: "Engineering (+30 Smarts, challenging)", effect: { smarts: 30, happiness: -10, major: 'Engineering' } },
                    { text: "Arts (+20 Happiness, creative)", effect: { happiness: 20, smarts: 5, major: 'Arts' } },
                    { text: "Medicine (+35 Health focus, rigorous)", effect: { health: 10, smarts: 35, happiness: -15, major: 'Medicine' } }
                ]
            },
            'find_spouse': {
                description: "You're ready to find that special someone! Who do you meet?",
                choices: [
                    { text: "Meet someone at a social gathering.", effect: { happiness: 20 }, nextEvent: 'propose_to_stranger' },
                    { text: "Try online dating.", effect: { happiness: 15, money: -100 }, nextEvent: 'propose_to_stranger' }
                ]
            },
            'propose_to_stranger': {
                description: "You've met someone nice! Are you ready to settle down?",
                choices: [
                    { text: "Propose marriage!💍", effect: { happiness: 30, money: -2000, isMarried: true }, condition: () => player.happiness >= 50 && currentAge >= 20 },
                    { text: "Just keep dating for now.", effect: { happiness: 15 } }
                ]
            },
            'child_birth': { // This event determines gender and branches to naming
                description: "Congratulations! You're having a baby!",
                choices: [
                    { text: "It's a Boy!", effect: {}, nextEvent: 'name_child_boy', action: (p) => p.pendingChildGender = 'boy' },
                    { text: "It's a Girl!", effect: {}, nextEvent: 'name_child_girl', action: (p) => p.pendingChildGender = 'girl' }
                ]
            },
            'name_child_boy': {
                description: "You had a beautiful baby boy! What will you name him?",
                choices: MALE_NAMES.map(name => ({
                    text: `Name him ${name}`,
                    effect: { happiness: 5 },
                    action: (p) => p.children.push({ name: name, gender: 'boy' })
                }))
            },
            'name_child_girl': {
                description: "You had a beautiful baby girl! What will you name her?",
                choices: FEMALE_NAMES.map(name => ({
                    text: `Name her ${name}`,
                    effect: { happiness: 5 },
                    action: (p) => p.children.push({ name: name, gender: 'girl' })
                }))
            }
        };


        // --- Core Game Functions ---

        /**
         * Initializes a new game with default player stats and new life milestones.
         */
        function initializeGame() {
            player = {
                health: 50,
                happiness: 50,
                smarts: 50,
                money: 1000,
                hasCar: false,
                hasHouse: false,
                isMarried: false,
                children: [], // Array to store { name: "...", gender: "..." }
                country: 'USA', // Starting country
                socialFollowers: 0,
                major: 'None', // No major initially
                pendingChildGender: null // Temporary for naming flow
            };
            currentAge = 0;
            gameOver = false;
            hideMessage(); // Hide any game over messages
            updateUI();
            displayEvent(getEventForAge(currentAge)); // Display the initial birth event
        }

        /**
         * Updates the UI to reflect current player stats and age.
         * Applies color coding to stats based on predefined thresholds.
         */
        function updateUI() {
            statHealth.textContent = player.health;
            statHappiness.textContent = player.happiness;
            statSmarts.textContent = player.smarts;
            statMoney.textContent = `$${player.money}`;
            currentAgeSpan.textContent = currentAge;

            // Update new stats
            statCar.textContent = player.hasCar ? 'Yes ✅' : 'No ❌';
            statHouse.textContent = player.hasHouse ? 'Yes ✅' : 'No ❌';
            statSpouse.textContent = player.isMarried ? 'Yes ❤️' : 'No 💔';
            // Correctly display children count and names
            statChildren.textContent = player.children.length > 0 ? `${player.children.length} (${player.children.map(c => c.name).join(', ')}) 👶` : 'None';
            statCountry.textContent = player.country;
            statSocialFollowers.textContent = player.socialFollowers;
            statMajor.textContent = player.major;

            // Apply color classes based on stat values
            statHealth.className = `stat-value ${getStatColorClass(player.health)}`;
            statHappiness.className = `stat-value ${getStatColorClass(player.happiness)}`;
            statSmarts.className = `stat-value ${getStatColorClass(player.smarts)}`;
            // Money is not color-coded by performance in this example, but could be.
            // For now, it's just value, could be good/bad if thresholds for wealth are set.
        }

        /**
         * Determines the CSS class for a stat value based on thresholds.
         * @param {number} value The stat value.
         * @returns {string} 'good', 'neutral', or 'bad'.
         */
        function getStatColorClass(value) {
            if (value >= STAT_THRESHOLD_GOOD) return 'good';
            if (value <= STAT_THRESHOLD_BAD) return 'bad';
            return 'neutral';
        }

        /**
         * Retrieves a random event appropriate for the current age, or a special event.
         * @param {number} age The current age of the player.
         * @param {string} [nextEventId] Optional ID for a specific next event to trigger.
         * @returns {object} An event object.
         */
        function getEventForAge(age, nextEventId = null) {
            if (nextEventId && specialEvents[nextEventId]) {
                return specialEvents[nextEventId];
            }

            // --- Special handling for age 17 university decision ---
            if (age === 17) {
                // Find the specific age 17 event and return it
                const age17Event = gameEvents[13].find(event => event.condition && event.condition() && event.description.includes("You're turning 17 soon!"));
                if (age17Event) {
                    return age17Event;
                }
            }
            // --- End special handling ---


            let eventsPool;
            if (age === 0) {
                eventsPool = gameEvents[0];
            } else if (age >= 6 && age < 13) {
                eventsPool = gameEvents[6];
            } else if (age >= 13 && age < 18) {
                // Filter out the age 17 specific event if currentAge is not 17, to avoid it appearing randomly
                eventsPool = gameEvents[13].filter(event => !(event.condition && event.description.includes("You're turning 17 soon!") && currentAge !== 17));
            } else if (age >= 18 && age < 30) {
                eventsPool = gameEvents[18];
            } else if (age >= 30 && age < 60) {
                eventsPool = gameEvents[30];
            } else if (age >= 60 && age < MAX_AGE) {
                eventsPool = gameEvents[60];
            } else {
                return null; // No more events defined for this age
            }

            // Filter events that have conditions and return true
            const availableEvents = eventsPool.filter(event => !event.condition || event.condition());
            if (availableEvents.length === 0) {
                // If all specific events have conditions that are not met,
                // pick a random event from the entire pool, ignoring conditions for fallback.
                // This prevents the game from getting stuck if conditions are too strict.
                return eventsPool[Math.floor(Math.random() * eventsPool.length)];
            }
            return availableEvents[Math.floor(Math.random() * availableEvents.length)];
        }

        /**
         * Displays the given event, updating the description and choice buttons.
         * @param {object} event The event object to display.
         */
        function displayEvent(event) {
            eventDescription.textContent = event.description;
            choicesGrid.innerHTML = ''; // Clear previous choices

            event.choices.forEach(choice => {
                const button = document.createElement('button');
                button.className = 'choice-button';
                button.textContent = choice.text;
                button.onclick = () => handleChoice(choice);
                // Disable button if it has a condition that is not met
                if (choice.condition && !choice.condition()) {
                    button.disabled = true;
                }
                choicesGrid.appendChild(button);
            });
        }

        /**
         * Handles the player's choice, applying effects and advancing the game.
         * @param {object} choice The chosen option object.
         */
        function handleChoice(choice) {
            if (gameOver) return;

            // Apply direct actions before effects, especially for complex state changes
            if (choice.action) {
                choice.action(player);
            }

            // Apply stat effects
            for (const stat in choice.effect) {
                if (player.hasOwnProperty(stat)) {
                    // Check for special 'chance' effect for money investments
                    if (stat === 'money' && choice.chance) {
                        if (Math.random() < choice.chance) { // Success!
                            player[stat] += choice.effect[stat];
                        } else { // Failure, lose some money
                            player[stat] -= (choice.effect[stat] / 2); // Example: lose half the potential gain
                        }
                    } else {
                        // Apply direct stat changes
                        player[stat] += choice.effect[stat];
                    }
                } else {
                    // Update new boolean/count/string properties like hasCar, major, etc.
                    player[stat] = choice.effect[stat];
                }
            }

            // Ensure stats don't go below 0 or above 100 (except money)
            player.health = Math.max(0, Math.min(100, player.health));
            player.happiness = Math.max(0, Math.min(100, player.happiness));
            player.smarts = Math.max(0, Math.min(100, player.smarts));
            player.money = Math.max(0, player.money); // Money can't go below 0

            let nextEventToDisplay = null;
            if (choice.nextEvent) {
                nextEventToDisplay = choice.nextEvent;
            }

            // Advance age, possibly by a 'jump'
            if (!nextEventToDisplay) { // Only advance age if not moving to a specific sequential event
                if (choice.nextAgeJump) {
                    currentAge = choice.nextAgeJump;
                } else {
                    currentAge += getRandomAgeJump(); // Advance a random number of years
                }
            }

            // If choosing university, ensure age jumps to 18 after making a choice from the payment options
            if ((nextEventToDisplay === 'choose_major' || nextEventToDisplay === 'university_payment_options') && currentAge === 17) {
                currentAge = 18; // Ensure age advances to 18 after university path is chosen
            }


            updateUI(); // Update display with new stats and age

            checkGameEnd(); // Check for game over conditions
            if (!gameOver) {
                // If a special nextEvent is specified, display it. Otherwise, get a random event for the new age.
                displayEvent(getEventForAge(currentAge, nextEventToDisplay));
            }
        }

        /**
         * Generates a random age jump (number of years to advance).
         * @returns {number} The number of years to advance.
         */
        function getRandomAgeJump() {
            // Jumps are smaller in early life, larger in later life
            if (currentAge < 18) return Math.floor(Math.random() * 3) + 1; // 1-3 years
            if (currentAge < 30) return Math.floor(Math.random() * 5) + 2; // 2-6 years
            if (currentAge < 60) return Math.floor(Math.random() * 7) + 3; // 3-9 years
            return Math.floor(Math.random() * 10) + 5; // 5-14 years for seniors
        }

        /**
         * Checks if any game over conditions are met (death, extreme stats).
         * Displays a game over message if applicable.
         */
        function checkGameEnd() {
            let message = "";
            let title = "Game Over!";

            if (currentAge >= MAX_AGE) {
                message = `You lived to the ripe old age of ${currentAge}! You had a long and full life.`;
                title = "A Full Life!";
                gameOver = true;
            } else if (player.health <= 0) {
                message = `Your health deteriorated rapidly. You died at age ${currentAge}.`;
                gameOver = true;
            } else if (player.happiness <= 0) {
                message = `Your life became unbearable. You passed away unhappily at age ${currentAge}.`;
                gameOver = true;
            } else if (player.money <= -50000) { // Severe debt condition
                message = `You fell into insurmountable debt. Your life ended in financial ruin at age ${currentAge}.`;
                gameOver = true;
            }

            if (gameOver) {
                showMessage(title, message);
                // Disable all choice buttons once game is over
                choicesGrid.innerHTML = '';
            }
        }

        /**
         * Displays a message box with a title and content, and shows the restart button.
         * @param {string} title The title of the message.
         * @param {string} content The main content of the message.
         */
        function showMessage(title, content) {
            messageBox.style.display = 'block';
            messageTitle.textContent = title;
            messageContent.textContent = content;
            restartGameButton.style.display = 'block';
        }

        /**
         * Hides the message box.
         */
        function hideMessage() {
            messageBox.style.display = 'none';
            restartGameButton.style.display = 'none';
        }

        // --- Event Listeners ---
        startButton.addEventListener('click', initializeGame);
        restartGameButton.addEventListener('click', initializeGame);
        themeToggle.addEventListener('click', toggleTheme);

        // --- Initial Setup (display the start button and apply theme) ---
        document.addEventListener('DOMContentLoaded', () => {
            const savedTheme = localStorage.getItem('lifeJumpsTheme');
            if (savedTheme === 'light') {
                isLightMode = true;
            } else {
                isLightMode = false; // Default to dark if no preference or 'dark' saved
            }
            applyTheme(); // Apply the saved or default theme
        });

    </script>
</body>
</html>

