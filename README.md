# Freelance-rate-calculator
Helping tool to calculate 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Freelance Rate Calculator - Price Your Services Right</title>
    <link href="https://fonts.googleapis.com/css2?family=Fraunces:wght@400;600;700&family=Inter:wght@400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --color-cream: #F8F6F1;
            --color-forest: #1A3A2E;
            --color-sage: #5D7363;
            --color-terracotta: #C85A3F;
            --color-gold: #D4A574;
            --color-charcoal: #2C2C2C;
            --color-light-sage: #E8EDE9;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--color-cream);
            color: var(--color-charcoal);
            line-height: 1.6;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* Decorative background elements */
        body::before {
            content: '';
            position: fixed;
            top: -50%;
            right: -20%;
            width: 800px;
            height: 800px;
            background: radial-gradient(circle, rgba(93, 115, 99, 0.08) 0%, transparent 70%);
            border-radius: 50%;
            z-index: 0;
            animation: float 20s ease-in-out infinite;
        }

        body::after {
            content: '';
            position: fixed;
            bottom: -30%;
            left: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(212, 165, 116, 0.06) 0%, transparent 70%);
            border-radius: 50%;
            z-index: 0;
            animation: float 25s ease-in-out infinite reverse;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(30px, -30px) rotate(5deg); }
            66% { transform: translate(-20px, 20px) rotate(-5deg); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 24px;
            position: relative;
            z-index: 1;
        }

        header {
            text-align: center;
            margin-bottom: 60px;
            animation: fadeInDown 0.8s ease-out;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h1 {
            font-family: 'Fraunces', serif;
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 700;
            color: var(--color-forest);
            margin-bottom: 16px;
            letter-spacing: -0.02em;
        }

        .subtitle {
            font-size: clamp(1.1rem, 2vw, 1.3rem);
            color: var(--color-sage);
            font-weight: 400;
            max-width: 600px;
            margin: 0 auto;
        }

        .calculator-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin-top: 40px;
            animation: fadeInUp 0.8s ease-out 0.2s both;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .input-panel, .result-panel {
            background: white;
            border-radius: 16px;
            padding: 48px;
            box-shadow: 0 4px 24px rgba(26, 58, 46, 0.08);
            position: relative;
            overflow: hidden;
        }

        .input-panel::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--color-terracotta), var(--color-gold));
        }

        .panel-title {
            font-family: 'Fraunces', serif;
            font-size: 1.75rem;
            font-weight: 600;
            color: var(--color-forest);
            margin-bottom: 32px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .panel-title::before {
            content: '';
            width: 6px;
            height: 6px;
            background: var(--color-terracotta);
            border-radius: 50%;
            display: inline-block;
        }

        .input-group {
            margin-bottom: 28px;
            animation: slideIn 0.5s ease-out both;
        }

        .input-group:nth-child(2) { animation-delay: 0.3s; }
        .input-group:nth-child(3) { animation-delay: 0.4s; }
        .input-group:nth-child(4) { animation-delay: 0.5s; }
        .input-group:nth-child(5) { animation-delay: 0.6s; }
        .input-group:nth-child(6) { animation-delay: 0.7s; }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        label {
            display: block;
            font-weight: 500;
            color: var(--color-forest);
            margin-bottom: 8px;
            font-size: 0.95rem;
        }

        .label-helper {
            font-size: 0.85rem;
            color: var(--color-sage);
            font-weight: 400;
            margin-left: 4px;
        }

        input {
            width: 100%;
            padding: 14px 16px;
            border: 2px solid var(--color-light-sage);
            border-radius: 8px;
            font-size: 1rem;
            font-family: 'Inter', sans-serif;
            transition: all 0.3s ease;
            background: var(--color-cream);
        }

        input:focus {
            outline: none;
            border-color: var(--color-terracotta);
            background: white;
            box-shadow: 0 0 0 4px rgba(200, 90, 63, 0.1);
        }

        input:hover {
            border-color: var(--color-sage);
        }

        .result-panel {
            display: flex;
            flex-direction: column;
            justify-content: center;
            background: linear-gradient(135deg, var(--color-forest) 0%, #2a5444 100%);
            color: white;
            position: relative;
        }

        .result-panel::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.05) 0%, transparent 70%);
            border-radius: 50%;
        }

        .result-main {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
            z-index: 1;
        }

        .result-label {
            font-size: 1rem;
            opacity: 0.8;
            margin-bottom: 12px;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 500;
        }

        .result-value {
            font-family: 'Fraunces', serif;
            font-size: clamp(3rem, 6vw, 4.5rem);
            font-weight: 700;
            line-height: 1;
            margin-bottom: 8px;
            color: var(--color-gold);
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
            transition: all 0.4s ease;
        }

        .result-value.updating {
            transform: scale(1.05);
        }

        .result-period {
            font-size: 1.1rem;
            opacity: 0.7;
        }

        .breakdown {
            background: rgba(255, 255, 255, 0.08);
            border-radius: 12px;
            padding: 24px;
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 1;
        }

        .breakdown-title {
            font-family: 'Fraunces', serif;
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 20px;
            color: var(--color-gold);
        }

        .breakdown-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .breakdown-item:last-child {
            border-bottom: none;
        }

        .breakdown-label {
            opacity: 0.85;
        }

        .breakdown-value {
            font-weight: 600;
            font-family: 'Fraunces', serif;
        }

        .tip-box {
            margin-top: 32px;
            padding: 20px 24px;
            background: var(--color-light-sage);
            border-left: 4px solid var(--color-terracotta);
            border-radius: 8px;
            animation: fadeIn 1s ease-out 0.8s both;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .tip-title {
            font-weight: 600;
            color: var(--color-forest);
            margin-bottom: 8px;
            font-size: 0.95rem;
        }

        .tip-text {
            font-size: 0.9rem;
            color: var(--color-sage);
            line-height: 1.6;
        }

        footer {
            text-align: center;
            margin-top: 80px;
            padding: 32px;
            color: var(--color-sage);
            font-size: 0.9rem;
        }

        @media (max-width: 968px) {
            .calculator-wrapper {
                grid-template-columns: 1fr;
            }

            .input-panel, .result-panel {
                padding: 32px 24px;
            }

            h1 {
                font-size: 2.5rem;
            }
        }

        @media (max-width: 640px) {
            .container {
                padding: 40px 16px;
            }

            h1 {
                font-size: 2rem;
            }

            .subtitle {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Freelance Rate Calculator</h1>
            <p class="subtitle">Calculate your ideal hourly rate based on your income goals, expenses, and billable hours</p>
        </header>

        <div class="calculator-wrapper">
            <div class="input-panel">
                <h2 class="panel-title">Your Details</h2>
                
                <div class="input-group">
                    <label for="desiredIncome">
                        Desired Annual Income
                        <span class="label-helper">(after taxes)</span>
                    </label>
                    <input type="number" id="desiredIncome" value="80000" min="0" step="1000">
                </div>

                <div class="input-group">
                    <label for="expenses">
                        Annual Business Expenses
                        <span class="label-helper">(software, equipment, etc.)</span>
                    </label>
                    <input type="number" id="expenses" value="12000" min="0" step="500">
                </div>

                <div class="input-group">
                    <label for="taxRate">
                        Tax Rate
                        <span class="label-helper">(%)</span>
                    </label>
                    <input type="number" id="taxRate" value="30" min="0" max="100" step="1">
                </div>

                <div class="input-group">
                    <label for="billableHours">
                        Billable Hours Per Week
                        <span class="label-helper">(realistic average)</span>
                    </label>
                    <input type="number" id="billableHours" value="30" min="1" max="168" step="1">
                </div>

                <div class="input-group">
                    <label for="weeksWorked">
                        Weeks Worked Per Year
                        <span class="label-helper">(account for vacation)</span>
                    </label>
                    <input type="number" id="weeksWorked" value="48" min="1" max="52" step="1">
                </div>

                <div class="input-group">
                    <label for="profitMargin">
                        Profit Margin
                        <span class="label-helper">(%)</span>
                    </label>
                    <input type="number" id="profitMargin" value="15" min="0" max="100" step="1">
                </div>

                <div class="tip-box">
                    <div class="tip-title">💡 Pro Tip</div>
                    <div class="tip-text">
                        Most freelancers can only bill 20-35 hours per week. The rest goes to admin, marketing, and business development.
                    </div>
                </div>
            </div>

            <div class="result-panel">
                <div class="result-main">
                    <div class="result-label">Your Hourly Rate</div>
                    <div class="result-value" id="hourlyRate">$75</div>
                    <div class="result-period">per hour</div>
                </div>

                <div class="breakdown">
                    <div class="breakdown-title">Breakdown</div>
                    <div class="breakdown-item">
                        <span class="breakdown-label">Annual Revenue Needed</span>
                        <span class="breakdown-value" id="annualRevenue">$143,333</span>
                    </div>
                    <div class="breakdown-item">
                        <span class="breakdown-label">Total Billable Hours/Year</span>
                        <span class="breakdown-value" id="totalHours">1,440</span>
                    </div>
                    <div class="breakdown-item">
                        <span class="breakdown-label">Daily Rate (8 hrs)</span>
                        <span class="breakdown-value" id="dailyRate">$600</span>
                    </div>
                    <div class="breakdown-item">
                        <span class="breakdown-label">Project Rate (40 hrs)</span>
                        <span class="breakdown-value" id="projectRate">$3,000</span>
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <p>Built for freelancers who value their worth. Set your rates with confidence.</p>
        </footer>
    </div>

    <script>
        // Get all input elements
        const inputs = {
            desiredIncome: document.getElementById('desiredIncome'),
            expenses: document.getElementById('expenses'),
            taxRate: document.getElementById('taxRate'),
            billableHours: document.getElementById('billableHours'),
            weeksWorked: document.getElementById('weeksWorked'),
            profitMargin: document.getElementById('profitMargin')
        };

        // Get result elements
        const results = {
            hourlyRate: document.getElementById('hourlyRate'),
            annualRevenue: document.getElementById('annualRevenue'),
            totalHours: document.getElementById('totalHours'),
            dailyRate: document.getElementById('dailyRate'),
            projectRate: document.getElementById('projectRate')
        };

        function formatCurrency(amount) {
            return new Intl.NumberFormat('en-US', {
                style: 'currency',
                currency: 'USD',
                minimumFractionDigits: 0,
                maximumFractionDigits: 0
            }).format(amount);
        }

        function formatNumber(num) {
            return new Intl.NumberFormat('en-US').format(num);
        }

        function calculate() {
            // Get values
            const desiredIncome = parseFloat(inputs.desiredIncome.value) || 0;
            const expenses = parseFloat(inputs.expenses.value) || 0;
            const taxRate = parseFloat(inputs.taxRate.value) / 100 || 0;
            const billableHours = parseFloat(inputs.billableHours.value) || 1;
            const weeksWorked = parseFloat(inputs.weeksWorked.value) || 1;
            const profitMargin = parseFloat(inputs.profitMargin.value) / 100 || 0;

            // Calculate total hours per year
            const totalHoursPerYear = billableHours * weeksWorked;

            // Calculate gross income needed (before taxes)
            const grossIncomeNeeded = desiredIncome / (1 - taxRate);

            // Add business expenses
            const revenueBeforeProfit = grossIncomeNeeded + expenses;

            // Add profit margin
            const totalRevenueNeeded = revenueBeforeProfit / (1 - profitMargin);

            // Calculate hourly rate
            const hourlyRate = totalRevenueNeeded / totalHoursPerYear;

            // Calculate other rates
            const dailyRate = hourlyRate * 8;
            const projectRate = hourlyRate * 40;

            // Update UI with animation
            results.hourlyRate.classList.add('updating');
            setTimeout(() => {
                results.hourlyRate.textContent = formatCurrency(hourlyRate);
                results.annualRevenue.textContent = formatCurrency(totalRevenueNeeded);
                results.totalHours.textContent = formatNumber(Math.round(totalHoursPerYear));
                results.dailyRate.textContent = formatCurrency(dailyRate);
                results.projectRate.textContent = formatCurrency(projectRate);
                results.hourlyRate.classList.remove('updating');
            }, 200);
        }

        // Add event listeners to all inputs
        Object.values(inputs).forEach(input => {
            input.addEventListener('input', calculate);
        });

        // Initial calculation
        calculate();
    </script>
</body>
</html>
