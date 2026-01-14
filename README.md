<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NOVA AI 4.5.0 | TikTok Verification</title>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        :root {
            --primary-purple: #a855f7;
            --primary-pink: #ec4899;
            --dark-bg: #020617;
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: var(--dark-bg);
            color: white;
            overflow-x: hidden;
            -webkit-tap-highlight-color: transparent;
            min-height: 100vh;
            position: relative;
        }
        
        .mesh-gradient {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: 
                radial-gradient(circle at 10% 10%, rgba(168, 85, 247, 0.15) 0%, transparent 40%),
                radial-gradient(circle at 90% 90%, rgba(236, 72, 153, 0.15) 0%, transparent 40%),
                radial-gradient(circle at 50% 50%, rgba(59, 130, 246, 0.1) 0%, transparent 50%);
            pointer-events: none;
        }
        
        .premium-headline-card {
            background: linear-gradient(135deg, rgba(168, 85, 247, 0.15) 0%, rgba(236, 72, 153, 0.1) 100%);
            border: 1px solid rgba(168, 85, 247, 0.4);
            box-shadow: 
                0 4px 6px -1px rgba(0, 0, 0, 0.1),
                0 2px 4px -1px rgba(0, 0, 0, 0.06),
                inset 0 1px 0 rgba(255, 255, 255, 0.05);
            position: relative;
            overflow: hidden;
        }
        
        .premium-headline-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                transparent,
                rgba(255, 255, 255, 0.1),
                transparent
            );
            animation: shimmer 3s infinite;
        }
        
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(200%); }
        }
        
        .glass-panel {
            background: var(--glass-bg);
            backdrop-filter: blur(20px) saturate(180%);
            -webkit-backdrop-filter: blur(20px) saturate(180%);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            box-shadow: 
                0 8px 32px rgba(0, 0, 0, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }
        
        .animate-reveal {
            animation: reveal 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
            opacity: 0;
            transform: translateY(20px);
        }
        
        @keyframes reveal {
            0% {
                opacity: 0;
                transform: translateY(30px) scale(0.95);
            }
            100% {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }
        
        .animate-fade-in {
            animation: fadeIn 0.6s ease-out forwards;
            opacity: 0;
        }
        
        @keyframes fadeIn {
            to {
                opacity: 1;
            }
        }
        
        .premium-btn {
            background: linear-gradient(135deg, var(--primary-purple) 0%, var(--primary-pink) 100%);
            background-size: 200% 200%;
            border: none;
            box-shadow: 
                0 10px 20px -5px rgba(168, 85, 247, 0.4),
                inset 0 1px 0 rgba(255, 255, 255, 0.2);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        
        .premium-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                transparent,
                rgba(255, 255, 255, 0.2),
                transparent
            );
            transition: left 0.6s;
        }
        
        .premium-btn:hover::before {
            left: 100%;
        }
        
        .premium-btn:hover {
            transform: translateY(-2px) scale(1.02);
            box-shadow: 
                0 15px 30px -8px rgba(168, 85, 247, 0.5),
                inset 0 1px 0 rgba(255, 255, 255, 0.3);
            background-position: right center;
        }
        
        .premium-btn:active {
            transform: translateY(0) scale(0.98);
            box-shadow: 
                0 5px 15px -3px rgba(168, 85, 247, 0.3),
                inset 0 2px 0 rgba(0, 0, 0, 0.1);
        }
        
        .gradient-text {
            background: linear-gradient(
                135deg,
                var(--primary-purple),
                var(--primary-pink),
                #3b82f6
            );
            background-size: 200% 200%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease infinite;
        }
        
        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        .pulse-border {
            position: relative;
            border: 2px solid transparent;
            background: linear-gradient(var(--dark-bg), var(--dark-bg)) padding-box,
                      linear-gradient(45deg, var(--primary-purple), var(--primary-pink)) border-box;
            animation: pulseGlow 2s infinite;
        }
        
        @keyframes pulseGlow {
            0%, 100% { 
                box-shadow: 
                    0 0 20px rgba(168, 85, 247, 0.3),
                    inset 0 0 20px rgba(168, 85, 247, 0.1);
            }
            50% { 
                box-shadow: 
                    0 0 40px rgba(168, 85, 247, 0.5),
                    inset 0 0 20px rgba(168, 85, 247, 0.2);
            }
        }
        
        .progress-container {
            width: 100%;
            height: 6px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-purple), var(--primary-pink));
            border-radius: 10px;
            transition: width 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        
        .progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                transparent,
                rgba(255, 255, 255, 0.4),
                transparent
            );
            animation: progressShimmer 1.5s infinite;
        }
        
        @keyframes progressShimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(200%); }
        }
        
        .puzzle-container {
            background: linear-gradient(
                135deg,
                rgba(168, 85, 247, 0.1),
                rgba(236, 72, 153, 0.05)
            );
            border: 1px solid rgba(168, 85, 247, 0.2);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            box-shadow: 
                0 10px 30px rgba(0, 0, 0, 0.2),
                inset 0 1px 0 rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }
        
        .puzzle-container:hover {
            transform: translateY(-5px);
            box-shadow: 
                0 20px 40px rgba(0, 0, 0, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
            border-color: rgba(168, 85, 247, 0.4);
        }
        
        .puzzle-input {
            background: rgba(0, 0, 0, 0.3);
            border: 2px solid rgba(168, 85, 247, 0.3);
            border-radius: 15px;
            padding: 1rem 1.5rem;
            font-size: 1.25rem;
            font-weight: 600;
            color: white;
            text-align: center;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            width: 100%;
            letter-spacing: 1px;
        }
        
        .puzzle-input::placeholder {
            color: rgba(255, 255, 255, 0.4);
            font-weight: 500;
        }
        
        .puzzle-input:focus {
            outline: none;
            border-color: var(--primary-purple);
            box-shadow: 
                0 0 0 3px rgba(168, 85, 247, 0.2),
                inset 0 2px 4px rgba(0, 0, 0, 0.2);
            background: rgba(0, 0, 0, 0.4);
            transform: scale(1.02);
        }
        
        .ad-simulation {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            border: 1px solid rgba(59, 130, 246, 0.3);
            border-radius: 20px;
            padding: 2rem;
            position: relative;
            overflow: hidden;
            box-shadow: 
                0 10px 30px rgba(0, 0, 0, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.05);
        }
        
        .ad-simulation::before {
            content: 'ADVERTISEMENT';
            position: absolute;
            top: 10px;
            right: 10px;
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            color: white;
            font-size: 0.6rem;
            font-weight: 700;
            padding: 4px 8px;
            border-radius: 4px;
            letter-spacing: 1px;
            text-transform: uppercase;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        
        .ad-simulation::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: repeating-linear-gradient(
                0deg,
                transparent,
                transparent 2px,
                rgba(255, 255, 255, 0.02) 2px,
                rgba(255, 255, 255, 0.02) 4px
            );
            pointer-events: none;
        }
        
        .letter-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 1.5rem 0;
            padding: 0.5rem;
        }
        
        .letter-tile {
            background: rgba(168, 85, 247, 0.15);
            border: 2px solid rgba(168, 85, 247, 0.3);
            border-radius: 12px;
            padding: 1rem;
            text-align: center;
            font-size: 1.5rem;
            font-weight: 700;
            color: white;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            user-select: none;
            position: relative;
            overflow: hidden;
        }
        
        .letter-tile::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                135deg,
                transparent,
                rgba(255, 255, 255, 0.1),
                transparent
            );
            transform: translateX(-100%);
            transition: transform 0.6s;
        }
        
        .letter-tile:hover::before {
            transform: translateX(100%);
        }
        
        .letter-tile:hover {
            background: rgba(168, 85, 247, 0.25);
            border-color: var(--primary-purple);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 
                0 5px 15px rgba(168, 85, 247, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }
        
        .letter-tile.selected {
            background: linear-gradient(135deg, var(--primary-purple), var(--primary-pink));
            border-color: white;
            color: white;
            transform: scale(1.1);
            box-shadow: 
                0 0 20px rgba(168, 85, 247, 0.5),
                inset 0 1px 0 rgba(255, 255, 255, 0.3);
        }
        
        .letter-tile.selected::after {
            content: '✓';
            position: absolute;
            top: -5px;
            right: -5px;
            background: white;
            color: var(--primary-purple);
            width: 20px;
            height: 20px;
            border-radius: 50%;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        
        .toast-notification {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: linear-gradient(135deg, var(--primary-purple), var(--primary-pink));
            color: white;
            padding: 1rem 2rem;
            border-radius: 15px;
            box-shadow: 
                0 20px 40px rgba(0, 0, 0, 0.3),
                0 0 20px rgba(168, 85, 247, 0.4);
            display: flex;
            align-items: center;
            gap: 0.75rem;
            z-index: 1000;
            animation: toastSlideIn 0.5s cubic-bezier(0.4, 0, 0.2, 1) forwards,
                     toastFloat 3s 0.5s ease-in-out infinite;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        @keyframes toastSlideIn {
            to {
                transform: translateX(-50%) translateY(0);
            }
        }
        
        @keyframes toastFloat {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-10px); }
        }
        
        .toast-notification::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, transparent, white, transparent);
            animation: toastShimmer 2s infinite;
        }
        
        @keyframes toastShimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        .step-indicator {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1.5rem;
            margin: 2rem 0;
            position: relative;
        }
        
        .step-indicator::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80%;
            height: 2px;
            background: rgba(255, 255, 255, 0.1);
            z-index: 0;
        }
        
        .step-dot {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            z-index: 1;
            transition: all 0.3s ease;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
        }
        
        .step-dot.active {
            background: linear-gradient(135deg, var(--primary-purple), var(--primary-pink));
            border-color: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
            box-shadow: 
                0 0 20px rgba(168, 85, 247, 0.4),
                inset 0 1px 0 rgba(255, 255, 255, 0.2);
        }
        
        .step-dot.completed {
            background: linear-gradient(135deg, #10b981, #059669);
            border-color: rgba(255, 255, 255, 0.3);
        }
        
        .code-display {
            background: linear-gradient(
                135deg,
                rgba(0, 0, 0, 0.4),
                rgba(0, 0, 0, 0.2)
            );
            border: 2px dashed rgba(168, 85, 247, 0.5);
            border-radius: 20px;
            padding: 1.5rem;
            position: relative;
            overflow: hidden;
        }
        
        .code-display::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(
                45deg,
                var(--primary-purple),
                var(--primary-pink),
                var(--primary-purple)
            );
            border-radius: 22px;
            z-index: -1;
            opacity: 0.3;
            animation: borderRotate 3s linear infinite;
        }
        
        @keyframes borderRotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .countdown-timer {
            font-family: 'Courier New', monospace;
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #fbbf24, #f59e0b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 2px 10px rgba(245, 158, 11, 0.3);
            letter-spacing: 2px;
        }
        
        .success-animation {
            animation: successPop 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes successPop {
            0% { transform: scale(0.8); opacity: 0; }
            70% { transform: scale(1.1); }
            100% { transform: scale(1); opacity: 1; }
        }
        
        .error-shake {
            animation: shake 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-5px); }
            20%, 40%, 60%, 80% { transform: translateX(5px); }
        }
        
        .floating-element {
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(2deg); }
        }
        
        .sparkle-effect {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: sparkle 2s infinite;
        }
        
        @keyframes sparkle {
            0%, 100% { 
                opacity: 0; 
                transform: scale(0); 
            }
            50% { 
                opacity: 1; 
                transform: scale(1); 
            }
        }
        
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: linear-gradient(45deg, var(--primary-purple), var(--primary-pink));
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
        }
        
        @media (max-width: 640px) {
            .letter-grid {
                grid-template-columns: repeat(3, 1fr);
                gap: 10px;
            }
            
            .step-indicator {
                gap: 1rem;
            }
            
            .step-dot {
                width: 40px;
                height: 40px;
            }
            
            .puzzle-container {
                padding: 1.5rem;
            }
            
            .puzzle-input {
                font-size: 1.1rem;
                padding: 0.875rem 1.25rem;
            }
        }
        
        @media (max-width: 480px) {
            .letter-grid {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .step-dot {
                width: 35px;
                height: 35px;
            }
        }
        
        /* Smooth animations for better performance */
        .smooth-transition {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1) !important;
        }
    </style>
</head>
<body>
    <div id="root"></div>
    <script type="text/babel">
        const { useState, useEffect, useRef } = React;

        const App = () => {
            // Main state management
            const [status, setStatus] = useState('idle');
            const [adTimer, setAdTimer] = useState(25);
            const [codeTimer, setCodeTimer] = useState(90);
            const [verificationCode, setVerificationCode] = useState('');
            const [showToast, setShowToast] = useState(false);
            const [toastMessage, setToastMessage] = useState('');
            const [puzzleAnswers, setPuzzleAnswers] = useState(['', '', '']);
            const [puzzleProgress, setPuzzleProgress] = useState(0);
            const [selectedLetters, setSelectedLetters] = useState([]);
            const [currentStep, setCurrentStep] = useState(0);
            const [showParticles, setShowParticles] = useState(false);
            const [copyIcon, setCopyIcon] = useState('copy'); // Track copy icon state
            const [userData, setUserData] = useState({
                sessionId: '',
                attempts: 0,
                completed: false,
                timestamp: null
            });

            // Puzzle question pools for variety
            const [mathQuestions, setMathQuestions] = useState([
                { question: "What is 5 + 3?", answer: "8", hint: "Simple addition between 5 and 3" },
                { question: "What is 7 × 2?", answer: "14", hint: "Seven times two" },
                { question: "What is 10 - 4?", answer: "6", hint: "Subtract 4 from 10" },
                { question: "What is 8 ÷ 2?", answer: "4", hint: "Eight divided by two" },
                { question: "What is 6 + 9?", answer: "15", hint: "Add six and nine" },
                { question: "What is 3 × 5?", answer: "15", hint: "Three times five" },
                { question: "What is 12 - 7?", answer: "5", hint: "Subtract seven from twelve" },
                { question: "What is 20 ÷ 5?", answer: "4", hint: "Twenty divided by five" },
                { question: "What is 4 + 11?", answer: "15", hint: "Add four and eleven" },
                { question: "What is 9 × 3?", answer: "27", hint: "Nine times three" }
            ]);

            const [wordQuestions, setWordQuestions] = useState([
                { letters: ['K', 'A', 'T'], answer: "CAT", hint: "A common household pet" },
                { letters: ['G', 'O', 'D'], answer: "DOG", hint: "Man's best friend" },
                { letters: ['A', 'R', 'C'], answer: "CAR", hint: "A vehicle for transportation" },
                { letters: ['U', 'P', 'C'], answer: "CUP", hint: "You drink from it" },
                { letters: ['O', 'S', 'H'], answer: "HOS", hint: "Opposite of stop (short form)" },
                { letters: ['I', 'P', 'N'], answer: "PIN", hint: "Used to secure things" },
                { letters: ['A', 'P', 'N'], answer: "PAN", hint: "Used for cooking" },
                { letters: ['O', 'B', 'X'], answer: "BOX", hint: "Container for items" },
                { letters: ['A', 'P', 'M'], answer: "MAP", hint: "Shows directions" },
                { letters: ['U', 'G', 'B'], answer: "BUG", hint: "Small insect" }
            ]);

            const [currentQuestions, setCurrentQuestions] = useState([]);

            // Refs for animations and effects
            const particleContainerRef = useRef(null);
            const successSoundRef = useRef(null);
            const errorSoundRef = useRef(null);
            const notificationSoundRef = useRef(null);
            const lucideIconsLoaded = useRef(false);

            // Initialize icons and effects on mount
            useEffect(() => {
                // Load Lucide icons
                const loadIcons = () => {
                    if (window.lucide && !lucideIconsLoaded.current) {
                        window.lucide.createIcons();
                        lucideIconsLoaded.current = true;
                    }
                };
                
                // Initial load
                loadIcons();
                
                // Re-run after component mounts
                setTimeout(loadIcons, 100);
                
                // Generate unique session ID
                const sessionId = 'NOVA-' + Date.now() + '-' + Math.random().toString(36).substr(2, 9);
                setUserData(prev => ({
                    ...prev,
                    sessionId,
                    timestamp: Date.now()
                }));
                
                // Generate random questions for this session
                generateRandomQuestions();
                
                // Create audio context for sounds
                if (typeof AudioContext !== 'undefined' || typeof webkitAudioContext !== 'undefined') {
                    const AudioContextClass = window.AudioContext || window.webkitAudioContext;
                    const audioContext = new AudioContextClass();
                    
                    // Success sound
                    successSoundRef.current = () => {
                        try {
                            const oscillator = audioContext.createOscillator();
                            const gainNode = audioContext.createGain();
                            
                            oscillator.connect(gainNode);
                            gainNode.connect(audioContext.destination);
                            
                            oscillator.frequency.setValueAtTime(523.25, audioContext.currentTime);
                            oscillator.frequency.exponentialRampToValueAtTime(659.25, audioContext.currentTime + 0.3);
                            
                            gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
                            gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
                            
                            oscillator.start();
                            oscillator.stop(audioContext.currentTime + 0.3);
                        } catch (e) {
                            console.log('Audio error:', e);
                        }
                    };
                    
                    // Error sound
                    errorSoundRef.current = () => {
                        try {
                            const oscillator = audioContext.createOscillator();
                            const gainNode = audioContext.createGain();
                            
                            oscillator.connect(gainNode);
                            gainNode.connect(audioContext.destination);
                            
                            oscillator.frequency.setValueAtTime(349.23, audioContext.currentTime);
                            oscillator.frequency.exponentialRampToValueAtTime(293.66, audioContext.currentTime + 0.2);
                            
                            gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
                            gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.2);
                            
                            oscillator.start();
                            oscillator.stop(audioContext.currentTime + 0.2);
                        } catch (e) {
                            console.log('Audio error:', e);
                        }
                    };
                }
                
                // Check for existing session data
                const savedData = localStorage.getItem('nova_session');
                if (savedData) {
                    try {
                        const parsed = JSON.parse(savedData);
                        if (parsed.expiry > Date.now()) {
                            setUserData(parsed);
                            setStatus(parsed.status || 'idle');
                            setPuzzleProgress(parsed.progress || 0);
                            setPuzzleAnswers(parsed.answers || ['', '', '']);
                            
                            // Load saved questions if available
                            if (parsed.questions) {
                                setCurrentQuestions(parsed.questions);
                            } else {
                                generateRandomQuestions();
                            }
                            
                            if (parsed.status === 'result' && parsed.code) {
                                setVerificationCode(parsed.code);
                                const timeLeft = Math.floor((parsed.expiry - Date.now()) / 1000);
                                if (timeLeft > 0) {
                                    setCodeTimer(timeLeft);
                                } else {
                                    resetSession();
                                }
                            }
                        } else {
                            localStorage.removeItem('nova_session');
                        }
                    } catch (e) {
                        console.error('Error loading session:', e);
                        localStorage.removeItem('nova_session');
                    }
                } else {
                    generateRandomQuestions();
                }
                
                // Refresh icons periodically
                const iconInterval = setInterval(() => {
                    if (window.lucide) {
                        window.lucide.createIcons();
                    }
                }, 2000);
                
                // Cleanup function
                return () => {
                    clearInterval(iconInterval);
                };
            }, []);

            // Generate random questions for each session
            const generateRandomQuestions = () => {
                // Pick 2 random math questions
                const shuffledMath = [...mathQuestions].sort(() => 0.5 - Math.random());
                const selectedMath = shuffledMath.slice(0, 2);
                
                // Pick 1 random word question
                const shuffledWord = [...wordQuestions].sort(() => 0.5 - Math.random());
                const selectedWord = shuffledWord[0];
                
                // Create questions array with mixed types
                const questions = [
                    {
                        id: 1,
                        title: "Basic Math",
                        question: selectedMath[0].question,
                        hint: selectedMath[0].hint,
                        answer: selectedMath[0].answer,
                        type: "math",
                        difficulty: "easy",
                        points: 10
                    },
                    {
                        id: 2,
                        title: "Word Puzzle",
                        question: `Arrange these letters to form a word: ${selectedWord.letters.join(' ')}`,
                        hint: selectedWord.hint,
                        answer: selectedWord.answer,
                        letters: selectedWord.letters,
                        type: "word",
                        difficulty: "easy",
                        points: 15
                    },
                    {
                        id: 3,
                        title: "Math Challenge",
                        question: selectedMath[1].question,
                        hint: selectedMath[1].hint,
                        answer: selectedMath[1].answer,
                        type: "math",
                        difficulty: "easy",
                        points: 10
                    }
                ];
                
                setCurrentQuestions(questions);
                return questions;
            };

            // Handle timer logic
            useEffect(() => {
                let intervalId;
                
                if (status === 'watching_ad' && adTimer > 0) {
                    intervalId = setInterval(() => {
                        setAdTimer(prev => {
                            if (prev <= 1) {
                                handleAdComplete();
                                return 0;
                            }
                            return prev - 1;
                        });
                    }, 1000);
                }
                
                if (status === 'result' && codeTimer > 0) {
                    intervalId = setInterval(() => {
                        setCodeTimer(prev => {
                            if (prev <= 1) {
                                resetSession();
                                return 0;
                            }
                            return prev - 1;
                        });
                    }, 1000);
                }
                
                return () => {
                    if (intervalId) clearInterval(intervalId);
                };
            }, [status, adTimer, codeTimer]);

            // Save session data when state changes
            useEffect(() => {
                const sessionData = {
                    ...userData,
                    status,
                    progress: puzzleProgress,
                    answers: puzzleAnswers,
                    questions: currentQuestions,
                    code: verificationCode,
                    expiry: Date.now() + (90 * 1000)
                };
                
                localStorage.setItem('nova_session', JSON.stringify(sessionData));
            }, [status, puzzleProgress, puzzleAnswers, verificationCode, userData, currentQuestions]);

            // Refresh icons when state changes
            useEffect(() => {
                if (window.lucide) {
                    setTimeout(() => window.lucide.createIcons(), 100);
                }
            }, [status, currentStep, copyIcon]);

            // Animation and particle effects
            useEffect(() => {
                if (showParticles && particleContainerRef.current) {
                    createParticleEffect();
                }
            }, [showParticles]);

            const createParticleEffect = () => {
                const container = particleContainerRef.current;
                if (!container) return;
                
                container.innerHTML = '';
                
                for (let i = 0; i < 50; i++) {
                    const particle = document.createElement('div');
                    particle.className = 'particle';
                    
                    const size = Math.random() * 6 + 2;
                    particle.style.width = `${size}px`;
                    particle.style.height = `${size}px`;
                    
                    const startX = Math.random() * 100;
                    const startY = Math.random() * 100;
                    
                    particle.style.left = `${startX}%`;
                    particle.style.top = `${startY}%`;
                    
                    const angle = Math.random() * Math.PI * 2;
                    const distance = Math.random() * 100 + 50;
                    
                    const endX = startX + Math.cos(angle) * distance;
                    const endY = startY + Math.sin(angle) * distance;
                    
                    const duration = Math.random() * 1 + 1;
                    
                    particle.animate([
                        {
                            transform: `translate(0, 0) scale(0)`,
                            opacity: 1
                        },
                        {
                            transform: `translate(${endX - startX}%, ${endY - startY}%) scale(1)`,
                            opacity: 0
                        }
                    ], {
                        duration: duration * 1000,
                        easing: 'cubic-bezier(0.4, 0, 0.2, 1)'
                    });
                    
                    container.appendChild(particle);
                    
                    setTimeout(() => {
                        if (particle.parentNode === container) {
                            container.removeChild(particle);
                        }
                    }, duration * 1000);
                }
                
                setTimeout(() => {
                    setShowParticles(false);
                }, 1000);
            };

            const showNotification = (message, type = 'success') => {
                setToastMessage(message);
                setShowToast(true);
                
                if (type === 'success' && successSoundRef.current) {
                    successSoundRef.current();
                } else if (type === 'error' && errorSoundRef.current) {
                    errorSoundRef.current();
                }
                
                setTimeout(() => {
                    setShowToast(false);
                }, 3000);
            };

            const startVerificationProcess = () => {
                setStatus('watching_ad');
                setAdTimer(25);
                setCurrentStep(1);
                setUserData(prev => ({
                    ...prev,
                    attempts: prev.attempts + 1,
                    timestamp: Date.now()
                }));
                
                // Generate new random questions for each attempt
                generateRandomQuestions();
                setPuzzleAnswers(['', '', '']);
                setSelectedLetters([]);
                
                showNotification('Verification process started!', 'success');
            };

            const handleAdComplete = () => {
                setStatus('puzzle1');
                setCurrentStep(2);
                setPuzzleProgress(33);
                showNotification('First puzzle unlocked!', 'success');
                setShowParticles(true);
            };

            const handlePuzzleInput = (index, value) => {
                const newAnswers = [...puzzleAnswers];
                newAnswers[index] = value;
                setPuzzleAnswers(newAnswers);
            };

            const handleLetterSelection = (letter) => {
                if (selectedLetters.includes(letter)) {
                    setSelectedLetters(selectedLetters.filter(l => l !== letter));
                } else {
                    setSelectedLetters([...selectedLetters, letter]);
                }
                
                const currentAnswer = selectedLetters.includes(letter) 
                    ? selectedLetters.filter(l => l !== letter).join('')
                    : [...selectedLetters, letter].join('');
                
                handlePuzzleInput(1, currentAnswer);
            };

            const submitPuzzleAnswer = (index) => {
                const userAnswer = puzzleAnswers[index].trim().toUpperCase();
                const puzzle = currentQuestions[index];
                const correctAnswer = puzzle.answer.toUpperCase();
                
                if (userAnswer === correctAnswer) {
                    // Success
                    const element = document.getElementById(`puzzle-${index}`);
                    if (element) {
                        element.classList.add('success-animation');
                    }
                    
                    const newProgress = Math.min(100, (index + 1) * 33);
                    setPuzzleProgress(newProgress);
                    
                    showNotification('Correct answer!', 'success');
                    
                    setTimeout(() => {
                        if (index < 2) {
                            const nextStatus = `puzzle${index + 2}`;
                            setStatus(nextStatus);
                            setCurrentStep(2 + index);
                        } else {
                            generateVerificationCode();
                        }
                    }, 800);
                    
                    setShowParticles(true);
                } else {
                    // Error
                    const inputElement = document.getElementById(`puzzle-input-${index}`);
                    if (inputElement) {
                        inputElement.classList.add('error-shake');
                        setTimeout(() => {
                            inputElement.classList.remove('error-shake');
                        }, 500);
                    }
                    
                    showNotification('Incorrect answer, try again!', 'error');
                }
            };

            const generateVerificationCode = () => {
                // Always ensure code ends with 7 and has different format each time
                const timestamp = Date.now();
                const randomPart = Math.floor(Math.random() * 10000).toString().padStart(4, '0');
                const sessionPart = userData.sessionId.slice(-3);
                
                // Different code formats for variety
                const formats = [
                    `NOVA-${timestamp.toString().slice(-5)}7-${randomPart}7`,
                    `NV${timestamp.toString().slice(-6)}-${randomPart}7`,
                    `NOVA${timestamp.toString().slice(-4)}-${sessionPart}${randomPart.slice(-1)}7`,
                    `NV${timestamp.toString().slice(-4)}${randomPart.slice(0,2)}-${sessionPart}7`
                ];
                
                const randomFormat = formats[Math.floor(Math.random() * formats.length)];
                setVerificationCode(randomFormat);
                
                setStatus('result');
                setCurrentStep(5);
                setCodeTimer(90);
                
                setUserData(prev => ({
                    ...prev,
                    completed: true,
                    completionTime: Date.now()
                }));
                
                showNotification('Verification code generated successfully!', 'success');
                setShowParticles(true);
            };

            const copyToClipboard = async () => {
                try {
                    await navigator.clipboard.writeText(verificationCode);
                    setCopyIcon('check');
                    showNotification('Code copied to clipboard!', 'success');
                    
                    setTimeout(() => {
                        setCopyIcon('copy');
                        if (window.lucide) {
                            window.lucide.createIcons();
                        }
                    }, 2000);
                } catch (err) {
                    // Fallback method
                    const textArea = document.createElement('textarea');
                    textArea.value = verificationCode;
                    document.body.appendChild(textArea);
                    textArea.select();
                    document.execCommand('copy');
                    document.body.removeChild(textArea);
                    
                    setCopyIcon('check');
                    showNotification('Code copied to clipboard!', 'success');
                    
                    setTimeout(() => {
                        setCopyIcon('copy');
                        if (window.lucide) {
                            window.lucide.createIcons();
                        }
                    }, 2000);
                }
            };

            const resetSession = () => {
                localStorage.removeItem('nova_session');
                setStatus('idle');
                setVerificationCode('');
                setAdTimer(25);
                setCodeTimer(90);
                setPuzzleAnswers(['', '', '']);
                setPuzzleProgress(0);
                setSelectedLetters([]);
                setCurrentStep(0);
                setCopyIcon('copy');
                
                // Generate new questions for new session
                generateRandomQuestions();
                
                const sessionId = 'NOVA-' + Date.now() + '-' + Math.random().toString(36).substr(2, 9);
                setUserData({
                    sessionId,
                    attempts: 0,
                    completed: false,
                    timestamp: Date.now()
                });
                
                showNotification('Session reset successfully!', 'success');
            };

            const renderAdSimulation = () => (
                <div className="ad-simulation animate-reveal">
                    <div className="flex flex-col items-center justify-center gap-6 py-4">
                        <div className="w-24 h-24 rounded-2xl bg-gradient-to-br from-blue-600 to-cyan-500 flex items-center justify-center shadow-2xl floating-element">
                            <i data-lucide="tv" className="w-12 h-12 text-white"></i>
                        </div>
                        
                        <div className="text-center">
                            <h3 className="text-2xl font-bold text-white mb-2">Advertisement</h3>
                            <p className="text-gray-400 text-sm max-w-md">
                                Please wait while we prepare your verification. This helps us maintain our premium service.
                            </p>
                        </div>
                        
                        <div className="w-full max-w-xs">
                            <div className="flex justify-between text-sm text-gray-400 mb-3">
                                <span className="flex items-center gap-2">
                                    <i data-lucide="clock" className="w-4 h-4"></i>
                                    Time remaining
                                </span>
                                <span className="font-bold text-xl text-purple-400">{adTimer}s</span>
                            </div>
                            
                            <div className="progress-container">
                                <div 
                                    className="progress-bar"
                                    style={{ width: `${((25 - adTimer) / 25) * 100}%` }}
                                ></div>
                            </div>
                            
                            <p className="text-gray-500 text-xs text-center mt-3">
                                Ads support our free verification service
                            </p>
                        </div>
                    </div>
                </div>
            );

            const renderPuzzle = (index) => {
                if (currentQuestions.length === 0) {
                    return <div className="text-center py-8">Loading puzzles...</div>;
                }
                
                const puzzle = currentQuestions[index];
                
                return (
                    <div id={`puzzle-${index}`} className="puzzle-container animate-reveal">
                        <div className="flex flex-col gap-6">
                            <div className="flex items-center justify-between">
                                <div className="flex items-center gap-4">
                                    <div className="step-dot active">
                                        <span className="text-white font-bold">{index + 1}</span>
                                    </div>
                                    <div>
                                        <h3 className="text-xl font-bold text-white">{puzzle.title}</h3>
                                        <p className="text-sm text-gray-400">Puzzle {index + 1} of 3</p>
                                    </div>
                                </div>
                                <div className="text-right">
                                    <div className="text-xs text-gray-400 mb-1">Difficulty</div>
                                    <div className="flex gap-1">
                                        {[...Array(3)].map((_, i) => (
                                            <div 
                                                key={i}
                                                className={`w-2 h-2 rounded-full ${i < (puzzle.difficulty === 'easy' ? 1 : puzzle.difficulty === 'medium' ? 2 : 3) ? 'bg-purple-500' : 'bg-gray-700'}`}
                                            ></div>
                                        ))}
                                    </div>
                                </div>
                            </div>
                            
                            <div className="glass-panel p-6">
                                <div className="text-center mb-6">
                                    <h4 className="text-2xl font-bold text-white mb-3">{puzzle.question}</h4>
                                    <p className="text-gray-400">
                                        <i data-lucide="lightbulb" className="w-4 h-4 inline mr-2"></i>
                                        {puzzle.hint}
                                    </p>
                                </div>
                                
                                {puzzle.type === 'word' ? (
                                    <div>
                                        <div className="letter-grid">
                                            {puzzle.letters.map((letter, idx) => (
                                                <div
                                                    key={idx}
                                                    className={`letter-tile ${selectedLetters.includes(letter) ? 'selected' : ''}`}
                                                    onClick={() => handleLetterSelection(letter)}
                                                >
                                                    {letter}
                                                </div>
                                            ))}
                                        </div>
                                        <p className="text-center text-gray-400 text-sm mb-4">
                                            Click letters to form the word
                                        </p>
                                    </div>
                                ) : null}
                                
                                <input
                                    id={`puzzle-input-${index}`}
                                    type="text"
                                    value={puzzleAnswers[index]}
                                    onChange={(e) => handlePuzzleInput(index, e.target.value)}
                                    className="puzzle-input mb-6"
                                    placeholder="Enter your answer here..."
                                    autoFocus
                                />
                                
                                <button
                                    onClick={() => submitPuzzleAnswer(index)}
                                    className="premium-btn w-full py-4 rounded-xl text-lg font-bold flex items-center justify-center gap-3"
                                >
                                    <i data-lucide="check" className="w-5 h-5"></i>
                                    Submit Answer
                                </button>
                            </div>
                            
                            <div className="flex justify-between items-center text-sm text-gray-400">
                                <div className="flex items-center gap-2">
                                    <i data-lucide="award" className="w-4 h-4 text-yellow-500"></i>
                                    <span>Points: {puzzle.points}</span>
                                </div>
                                <div className="flex items-center gap-2">
                                    <i data-lucide="help-circle" className="w-4 h-4"></i>
                                    <span>Need help? Try to solve it!</span>
                                </div>
                            </div>
                        </div>
                    </div>
                );
            };

            const renderVerificationCode = () => (
                <div className="space-y-6 animate-reveal">
                    <div className="text-center">
                        <div className="w-24 h-24 rounded-full bg-gradient-to-br from-green-500 to-emerald-500 flex items-center justify-center mx-auto mb-6 success-animation">
                            <i data-lucide="check-circle" className="w-12 h-12 text-white"></i>
                        </div>
                        <h3 className="text-2xl font-bold text-white mb-2">Verification Complete!</h3>
                        <p className="text-gray-400 max-w-md mx-auto">
                            Your premium verification code has been generated. Use it within the time limit.
                        </p>
                    </div>
                    
                    <div className="code-display">
                        <div className="flex items-center justify-between mb-4">
                            <div>
                                <div className="text-xs text-gray-400 uppercase tracking-widest mb-1">Your Verification Code</div>
                                <div className="text-3xl font-mono font-bold text-white tracking-wider">
                                    {verificationCode}
                                </div>
                            </div>
                            <button
                                onClick={copyToClipboard}
                                className="premium-btn w-14 h-14 rounded-xl flex items-center justify-center hover:scale-110 transition-transform"
                            >
                                <i data-lucide={copyIcon} className="w-6 h-6"></i>
                            </button>
                        </div>
                        
                        <div className="text-center pt-4 border-t border-gray-800">
                            <div className="flex items-center justify-center gap-3 mb-3">
                                <i data-lucide="clock" className="w-5 h-5 text-yellow-500"></i>
                                <span className="text-sm text-gray-400">Expires in:</span>
                            </div>
                            <div className="countdown-timer">
                                00:{codeTimer < 10 ? `0${codeTimer}` : codeTimer}
                            </div>
                            <p className="text-xs text-gray-500 mt-2">
                                Copy and use this code in our Telegram group
                            </p>
                        </div>
                    </div>
                    
                    <a
                        href="https://t.me/tiknova1premium7ultra"
                        target="_blank"
                        rel="noopener noreferrer"
                        className="premium-btn w-full py-4 rounded-xl text-lg font-bold flex items-center justify-center gap-3 hover:scale-[1.02] transition-transform"
                    >
                        <i data-lucide="send" className="w-5 h-5"></i>
                        Use Code in Telegram
                    </a>
                    
                    <button
                        onClick={resetSession}
                        className="w-full py-3 bg-gray-800 hover:bg-gray-700 text-gray-400 hover:text-white rounded-xl font-medium transition-all duration-300"
                    >
                        Generate New Code
                    </button>
                </div>
            );

            return (
                <div className="min-h-screen flex flex-col items-center justify-center p-4 md:p-6 relative overflow-hidden">
                    <div className="mesh-gradient"></div>
                    <div ref={particleContainerRef} className="sparkle-effect"></div>
                    
                    <div className="w-full max-w-md mx-auto relative z-10">
                        <div className="text-center mb-8">
                            <div className="flex justify-center mb-6">
                                <div className="w-20 h-20 rounded-2xl bg-gradient-to-br from-purple-600 to-pink-500 flex items-center justify-center shadow-2xl pulse-border floating-element">
                                    <i data-lucide="zap" className="w-10 h-10 text-white"></i>
                                </div>
                            </div>
                            <h1 className="text-4xl font-black tracking-tighter text-white mb-2">
                                NOVA <span className="gradient-text">AI 4.5.0</span>
                            </h1>
                            <p className="text-gray-400 font-medium">
                                Premium TikTok Verification System
                            </p>
                        </div>
                        
                        <div className="premium-headline-card rounded-3xl p-6 mb-8">
                            <div className="flex flex-col items-center gap-4">
                                <div className="px-4 py-2 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full text-xs font-black uppercase tracking-widest text-white shadow-lg">
                                    Premium Verification
                                </div>
                                <p className="text-white font-extrabold text-center text-lg leading-relaxed">
                                    Complete 3 easy puzzles to get your verification code!
                                </p>
                                <div className="flex items-center gap-2 text-sm text-purple-300">
                                    <i data-lucide="shield" className="w-4 h-4"></i>
                                    <span>100% Secure • Instant Delivery</span>
                                </div>
                            </div>
                        </div>
                        
                        <div className="step-indicator mb-8">
                            <div className={`step-dot ${currentStep >= 1 ? 'active' : ''}`}>
                                <i data-lucide="play" className="w-5 h-5"></i>
                            </div>
                            <div className={`step-dot ${currentStep >= 2 ? 'active' : ''}`}>
                                <i data-lucide="puzzle" className="w-5 h-5"></i>
                            </div>
                            <div className={`step-dot ${currentStep >= 3 ? 'active' : ''}`}>
                                <span className="text-white font-bold">1</span>
                            </div>
                            <div className={`step-dot ${currentStep >= 4 ? 'active' : ''}`}>
                                <span className="text-white font-bold">2</span>
                            </div>
                            <div className={`step-dot ${currentStep >= 5 ? 'completed' : ''}`}>
                                <i data-lucide="check" className="w-5 h-5"></i>
                            </div>
                        </div>
                        
                        {status === 'idle' && (
                            <div className="space-y-6 animate-reveal">
                                <div className="glass-panel p-6">
                                    <h3 className="text-xl font-bold text-white mb-4 flex items-center gap-3">
                                        <i data-lucide="info" className="w-5 h-5 text-purple-500"></i>
                                        How It Works
                                    </h3>
                                    <div className="space-y-4">
                                        <div className="flex gap-4">
                                            <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-purple-600/20 to-pink-600/20 border border-purple-500/30 flex items-center justify-center flex-shrink-0">
                                                <span className="text-sm font-bold text-purple-400">1</span>
                                            </div>
                                            <div>
                                                <p className="text-white font-semibold">Watch Advertisement</p>
                                                <p className="text-gray-400 text-sm">Wait 25 seconds for ad verification</p>
                                            </div>
                                        </div>
                                        <div className="flex gap-4">
                                            <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-purple-600/20 to-pink-600/20 border border-purple-500/30 flex items-center justify-center flex-shrink-0">
                                                <span className="text-sm font-bold text-purple-400">2</span>
                                            </div>
                                            <div>
                                                <p className="text-white font-semibold">Solve 3 Easy Puzzles</p>
                                                <p className="text-gray-400 text-sm">Simple math and word puzzles</p>
                                            </div>
                                        </div>
                                        <div className="flex gap-4">
                                            <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-purple-600/20 to-pink-600/20 border border-purple-500/30 flex items-center justify-center flex-shrink-0">
                                                <span className="text-sm font-bold text-purple-400">3</span>
                                            </div>
                                            <div>
                                                <p className="text-white font-semibold">Get Your Code</p>
                                                <p className="text-gray-400 text-sm">Receive verification code instantly</p>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                
                                <button
                                    onClick={startVerificationProcess}
                                    className="premium-btn w-full py-5 rounded-2xl text-xl font-black flex items-center justify-center gap-3"
                                >
                                    <i data-lucide="zap" className="w-6 h-6"></i>
                                    Start Verification
                                    <i data-lucide="chevron-right" className="w-5 h-5"></i>
                                </button>
                                
                                <div className="text-center text-sm text-gray-500">
                                    <p>Session ID: {userData.sessionId}</p>
                                    <p>Each attempt has different puzzles!</p>
                                </div>
                            </div>
                        )}
                        
                        {status === 'watching_ad' && renderAdSimulation()}
                        {status === 'puzzle1' && renderPuzzle(0)}
                        {status === 'puzzle2' && renderPuzzle(1)}
                        {status === 'puzzle3' && renderPuzzle(2)}
                        {status === 'result' && renderVerificationCode()}
                        
                        <div className="mt-8 text-center">
                            <div className="flex items-center justify-center gap-4 text-xs text-gray-600">
                                <span>© 2024 NOVA AI</span>
                                <span>•</span>
                                <span>Version 4.5.0</span>
                                <span>•</span>
                                <span>Premium System</span>
                            </div>
                            <p className="text-gray-700 text-xs mt-2">
                                Attempts: {userData.attempts} • Status: {status}
                            </p>
                        </div>
                    </div>
                    
                    {showToast && (
                        <div className="toast-notification">
                            <i data-lucide="check-circle" className="w-5 h-5 text-white"></i>
                            <span className="font-bold">{toastMessage}</span>
                        </div>
                    )}
                    
                    <div className="fixed inset-0 pointer-events-none">
                        {[...Array(20)].map((_, i) => (
                            <div
                                key={i}
                                className="sparkle"
                                style={{
                                    left: `${Math.random() * 100}%`,
                                    top: `${Math.random() * 100}%`,
                                    animationDelay: `${Math.random() * 2}s`,
                                    animationDuration: `${Math.random() * 1 + 1}s`
                                }}
                            ></div>
                        ))}
                    </div>
                </div>
            );
        };

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
