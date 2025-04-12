<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Calculate and convert between different calendar eras and time periods with our easy-to-use Era Calculator." />
    <meta name="keywords" content="era calculator, time period conversion, historical calendar, BCE CE calculator, year converter" />
    <title>Era Calculator - Convert Between Calendar Systems</title>
    <style>
        /* Modern CSS with Custom Variables */
        :root {
            --primary-blue: #3f51b5;
            --secondary-teal: #009688;
            --accent-amber: #ffc107;
            --light-bg: #f5f7fa;
            --card-bg: #ffffff;
            --dark-text: #333333;
            --medium-text: #666666;
            --light-text: #f5f7fa;
            --border-color: #e0e0e0;
            --success-green: #4caf50;
            --error-red: #f44336;
            --shadow-sm: 0 2px 8px rgba(0,0,0,0.1);
            --shadow-md: 0 4px 12px rgba(0,0,0,0.15);
            --transition-fast: all 0.2s ease;
            --border-radius: 8px;
            --max-width: 1000px;
        }
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        }
        body {
            background-color: var(--light-bg);
            color: var(--dark-text);
            line-height: 1.6;
        }
        .era-container {
            max-width: var(--max-width);
            margin: 0 auto;
            padding: 1.5rem;
            background: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-sm);
        }
        .era-header {
            text-align: center;
            margin-bottom: 2rem;
            padding: 1rem;
            background: linear-gradient(135deg, var(--primary-blue), var(--secondary-teal));
            color: var(--light-text);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-md);
        }
        .era-title {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
        }
        .era-subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        .era-tabs {
            display: flex;
            margin-bottom: 1.5rem;
            border-bottom: 2px solid var(--border-color);
            overflow-x: auto;
            scrollbar-width: thin;
        }
        .era-tab {
            padding: 0.8rem 1.2rem;
            cursor: pointer;
            border: none;
            background: none;
            font-size: 1rem;
            font-weight: 600;
            color: var(--medium-text);
            transition: var(--transition-fast);
            white-space: nowrap;
        }
        .era-tab:hover {
            color: var(--primary-blue);
        }
        .era-tab.active {
            color: var(--primary-blue);
            border-bottom: 3px solid var(--primary-blue);
            margin-bottom: -2px;
        }
        .era-tab-content {
            display: none;
            padding: 1rem 0;
        }
        .era-tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .era-form-group {
            margin-bottom: 1.5rem;
        }
        .era-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--primary-blue);
        }
        .era-input, .era-select {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid var(--border-color);
            border-radius: var(--border-radius);
            font-size: 1rem;
            transition: var(--transition-fast);
            background-color: var(--light-bg);
        }
        .era-input:focus, .era-select:focus {
            outline: none;
            border-color: var(--primary-blue);
            background-color: var(--card-bg);
            box-shadow: 0 0 0 3px rgba(63, 81, 181, 0.2);
        }
        .era-input-group {
            display: flex;
            gap: 1rem;
        }
        .era-input-group .era-form-group {
            flex: 1;
        }
        .era-button {
            width: 100%;
            padding: 1rem;
            border: none;
            border-radius: var(--border-radius);
            background-color: var(--primary-blue);
            color: var(--light-text);
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition-fast);
            box-shadow: var(--shadow-sm);
            margin-top: 1rem;
        }
        .era-button:hover {
            background-color: var(--secondary-teal);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }
        .era-button:active {
            transform: translateY(0);
        }
        .era-result {
            margin-top: 2rem;
            padding: 1.5rem;
            border-radius: var(--border-radius);
            background-color: var(--light-bg);
            border-left: 4px solid var(--secondary-teal);
        }
        .era-result-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: var(--secondary-teal);
        }
        .era-result-item {
            margin-bottom: 0.8rem;
            padding-bottom: 0.8rem;
            border-bottom: 1px solid var(--border-color);
        }
        .era-result-item:last-child {
            margin-bottom: 0;
            padding-bottom: 0;
            border-bottom: none;
        }
        .era-result-label {
            font-weight: 600;
            margin-right: 0.5rem;
        }
        .era-result-value {
            font-weight: normal;
        }
        .era-info-section {
            margin-top: 2.5rem;
            padding-top: 1.5rem;
            border-top: 1px solid var(--border-color);
        }
        .era-info-title {
            font-size: 1.5rem;
            color: var(--primary-blue);
            margin-bottom: 1rem;
        }
        .era-info-text {
            margin-bottom: 1rem;
        }
        .era-era-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
            margin: 1.5rem 0;
        }
        .era-era-item {
            padding: 1rem;
            background-color: var(--light-bg);
            border-radius: var(--border-radius);
            border-left: 3px solid var(--accent-amber);
        }
        .era-era-title {
            font-weight: 600;
            color: var(--dark-text);
            margin-bottom: 0.3rem;
        }
        .era-era-years {
            font-size: 0.9rem;
            color: var(--medium-text);
        }
        .error-message {
            color: var(--error-red);
            font-size: 0.9rem;
            margin-top: 0.5rem;
            display: none;
        }
        /* Responsive Styles */
        @media (max-width: 768px) {
            .era-container {
                padding: 1rem;
            }
            .era-header {
                padding: 0.8rem;
            }
            .era-title {
                font-size: 1.8rem;
            }
            .era-subtitle {
                font-size: 1rem;
            }
            .era-input-group {
                flex-direction: column;
                gap: 0.5rem;
            }
        }
        @media (max-width: 480px) {
            body {
                padding: 0.5rem;
            }
            .era-container {
                padding: 0.8rem;
            }
            .era-title {
                font-size: 1.5rem;
            }
            .era-subtitle {
                font-size: 0.9rem;
            }
            .era-tab {
                padding: 0.6rem 1rem;
                font-size: 0.9rem;
            }
            .era-result {
                padding: 1rem;
            }
            .era-result-title {
                font-size: 1.1rem;
            }
            .era-era-list {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="era-container">
        <header class="era-header">
            <h1 class="era-title">Era Calculator</h1>
            <p class="era-subtitle">Convert dates between historical time periods and calendar systems</p>
        </header>
        <div class="era-tabs">
            <button class="era-tab active" data-tab="convert">Date Converter</button>
            <button class="era-tab" data-tab="era-finder">Era Finder</button>
            <button class="era-tab" data-tab="age-calc">Age Calculator</button>
            <button class="era-tab" data-tab="timeline">Historical Timeline</button>
        </div>
        <div id="convert" class="era-tab-content active">
            <form id="converter-form">
                <div class="era-form-group">
                    <label for="date-input" class="era-label">Enter Date</label>
                    <input type="date" id="date-input" class="era-input" value="2025-04-12">
                </div>
                <div class="era-form-group">
                    <label for="from-calendar" class="era-label">From Calendar System</label>
                    <select id="from-calendar" class="era-select">
                        <option value="gregorian">Gregorian (Current)</option>
                        <option value="julian">Julian</option>
                        <option value="hebrew">Hebrew</option>
                        <option value="islamic">Islamic/Hijri</option>
                        <option value="buddhist">Buddhist</option>
                    </select>
                </div>
                <div class="era-form-group">
                    <label for="to-calendar" class="era-label">To Calendar System</label>
                    <select id="to-calendar" class="era-select">
                        <option value="gregorian">Gregorian</option>
                        <option value="julian">Julian</option>
                        <option value="hebrew">Hebrew</option>
                        <option value="islamic">Islamic/Hijri</option>
                        <option value="buddhist">Buddhist</option>
                        <option value="all">All Calendar Systems</option>
                    </select>
                </div>
                <button type="button" class="era-button" id="convert-btn">Convert Date</button>
            </form>
            <div class="era-result" id="conversion-result">
                <h3 class="era-result-title">Conversion Results</h3>
                <div class="era-result-item">
                    <span class="era-result-label">Gregorian:</span>
                    <span class="era-result-value" id="gregorian-value">April 12, 2025 CE</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Julian:</span>
                    <span class="era-result-value" id="julian-value">March 30, 2025 CE</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Hebrew:</span>
                    <span class="era-result-value" id="hebrew-value">13 Nisan, 5785</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Islamic:</span>
                    <span class="era-result-value" id="islamic-value">13 Shawwal, 1446 AH</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Buddhist:</span>
                    <span class="era-result-value" id="buddhist-value">April 12, 2568 BE</span>
                </div>
            </div>
        </div>
        <div id="era-finder" class="era-tab-content">
            <form id="era-finder-form">
                <div class="era-input-group">
                    <div class="era-form-group">
                        <label for="year-input" class="era-label">Year</label>
                        <input type="number" id="year-input" class="era-input" placeholder="e.g. 1066">
                    </div>
                    <div class="era-form-group">
                        <label for="era-type" class="era-label">Era Type</label>
                        <select id="era-type" class="era-select">
                            <option value="ce">CE/AD</option>
                            <option value="bce">BCE/BC</option>
                        </select>
                    </div>
                </div>
                <div class="era-form-group">
                    <label for="region" class="era-label">Region (Optional)</label>
                    <select id="region" class="era-select">
                        <option value="global">Global</option>
                        <option value="europe">Europe</option>
                        <option value="asia">Asia</option>
                        <option value="america">Americas</option>
                        <option value="africa">Africa</option>
                        <option value="middle-east">Middle East</option>
                    </select>
                </div>
                <button type="button" class="era-button" id="find-era-btn">Find Historical Era</button>
                <p class="error-message" id="era-error">Please enter a valid year</p>
            </form>
            <div class="era-result" id="era-result">
                <h3 class="era-result-title">Historical Era</h3>
                <div class="era-result-item">
                    <span class="era-result-label">Primary Era:</span>
                    <span class="era-result-value" id="primary-era">Modern Era (1900 CE - Present)</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Sub-period:</span>
                    <span class="era-result-value" id="sub-era">Information Age (1970 CE - Present)</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Contemporary With:</span>
                    <span class="era-result-value" id="contemporary-eras">
                        Atomic Age, Space Age, Digital Revolution
                    </span>
                </div>
            </div>
        </div>
        <div id="age-calc" class="era-tab-content">
            <form id="age-calculator-form">
                <div class="era-form-group">
                    <label for="birth-date" class="era-label">Birth Date</label>
                    <input type="date" id="birth-date" class="era-input">
                </div>
                <div class="era-form-group">
                    <label for="calculation-date" class="era-label">Calculate Age As Of</label>
                    <select id="calculation-date-type" class="era-select">
                        <option value="today">Today</option>
                        <option value="specific">Specific Date</option>
                    </select>
                </div>
                <div class="era-form-group" id="specific-date-group" style="display:none;">
                    <label for="specific-date" class="era-label">Specific Date</label>
                    <input type="date" id="specific-date" class="era-input">
                </div>
                <button type="button" class="era-button" id="calculate-age-btn">Calculate Age</button>
                <p class="error-message" id="age-error">Please enter a valid birth date</p>
            </form>
            <div class="era-result" id="age-result">
                <h3 class="era-result-title">Age Calculation Results</h3>
                <div class="era-result-item">
                    <span class="era-result-label">Age:</span>
                    <span class="era-result-value" id="age-years">35 years, 2 months, 15 days</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Total Days:</span>
                    <span class="era-result-value" id="age-days">12,875 days</span>
                </div>
                <div class="era-result-item">
                    <span class="era-result-label">Born During:</span>
                    <span class="era-result-value" id="birth-era">Information Age</span>
                </div>
            </div>
        </div>
        <div id="timeline" class="era-tab-content">
            <div class="era-form-group">
                <label for="era-filter" class="era-label">Filter By Region</label>
                <select id="era-filter" class="era-select">
                    <option value="all">All Regions</option>
                    <option value="global">Global</option>
                    <option value="europe">Europe</option>
                    <option value="asia">Asia</option>
                    <option value="america">Americas</option>
                    <option value="africa">Africa</option>
                    <option value="middle-east">Middle East</option>
                </select>
            </div>
            <div class="era-result">
                <h3 class="era-result-title">Historical Eras Timeline</h3>
                <h4 class="era-info-title">Ancient History</h4>
                <div class="era-era-list" id="ancient-list">
                    <div class="era-era-item">
                        <div class="era-era-title">Stone Age</div>
                        <div class="era-era-years">3.4 Million BCE - 3000 BCE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Bronze Age</div>
                        <div class="era-era-years">3000 BCE - 1200 BCE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Iron Age</div>
                        <div class="era-era-years">1200 BCE - 500 BCE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Classical Antiquity</div>
                        <div class="era-era-years">800 BCE - 600 CE</div>
                    </div>
                </div>
                <h4 class="era-info-title">Middle Ages</h4>
                <div class="era-era-list" id="medieval-list">
                    <div class="era-era-item">
                        <div class="era-era-title">Early Middle Ages</div>
                        <div class="era-era-years">500 CE - 1000 CE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">High Middle Ages</div>
                        <div class="era-era-years">1000 CE - 1250 CE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Late Middle Ages</div>
                        <div class="era-era-years">1250 CE - 1500 CE</div>
                    </div>
                </div>
                <h4 class="era-info-title">Modern History</h4>
                <div class="era-era-list" id="modern-list">
                    <div class="era-era-item">
                        <div class="era-era-title">Renaissance</div>
                        <div class="era-era-years">1400 CE - 1600 CE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Age of Discovery</div>
                        <div class="era-era-years">1400 CE - 1700 CE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Industrial Revolution</div>
                        <div class="era-era-years">1760 CE - 1840 CE</div>
                    </div>
                    <div class="era-era-item">
                        <div class="era-era-title">Information Age</div>
                        <div class="era-era-years">1970 CE - Present</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="era-info-section">
            <h2 class="era-info-title">About Era Calculations</h2>
            <p class="era-info-text">
                An era is a period of time marked by distinctive character, events, or characteristics. Historical eras are typically defined by major technological, cultural, or political shifts.
            </p>
            <p class="era-info-text">
                Our Era Calculator allows you to:
            </p>
            <ul>
                <li>Convert dates between different calendar systems including Gregorian, Julian, Hebrew, Islamic, and Buddhist calendars</li>
                <li>Identify which historical era a specific year belongs to</li>
                <li>Calculate age between two dates across different eras</li>
                <li>Explore a comprehensive timeline of major historical periods</li>
            </ul>
            <p class="era-info-text">
                Calendar conversions are approximate, especially for dates prior to calendar reforms. The Gregorian calendar was adopted at different times in different regions, with the transition from the Julian calendar occurring as late as the 20th century in some countries.
            </p>
        </div>
    </div>
    
    <script>
    // DOM Elements
const tabs = document.querySelectorAll('.era-tab');
const tabContents = document.querySelectorAll('.era-tab-content');
const calculationDateType = document.getElementById('calculation-date-type');
const specificDateGroup = document.getElementById('specific-date-group');

// Event Listeners
tabs.forEach(tab => {
    tab.addEventListener('click', () => {
        // Deactivate all tabs
        tabs.forEach(t => t.classList.remove('active'));
        tabContents.forEach(content => content.classList.remove('active'));
        // Activate clicked tab
        tab.classList.add('active');
        const tabId = tab.getAttribute('data-tab');
        document.getElementById(tabId).classList.add('active');
    });
});

calculationDateType.addEventListener('change', () => {
    specificDateGroup.style.display = 
        calculationDateType.value === 'specific' ? 'block' : 'none';
});

// Date Converter Functionality
const convertBtn = document.getElementById('convert-btn');
convertBtn.addEventListener('click', convertDate);

function convertDate() {
    const dateInput = document.getElementById('date-input').value;
    const fromCalendar = document.getElementById('from-calendar').value;
    const toCalendar = document.getElementById('to-calendar').value;
    // In a real implementation, we would use proper calendar conversion algorithms
    // This is a simplified demonstration
    const date = new Date(dateInput);
    const gregorianDate = date.toLocaleDateString('en-US', { 
        year: 'numeric', 
        month: 'long', 
        day: 'numeric' 
    });
    // Simple approximations for demonstration
    const julianDay = new Date(date.getTime() - (13 * 24 * 60 * 60 * 1000));
    const julianDate = julianDay.toLocaleDateString('en-US', { 
        year: 'numeric', 
        month: 'long', 
        day: 'numeric' 
    });
    // Update result view
    document.getElementById('gregorian-value').textContent = `${gregorianDate} CE`;
    document.getElementById('julian-value').textContent = `${julianDate} CE`;
    document.getElementById('hebrew-value').textContent = `13 Nisan, ${date.getFullYear() + 3760}`;
    document.getElementById('islamic-value').textContent = `13 Shawwal, ${Math.floor((date.getFullYear() - 622) * 1.03)} AH`;
    document.getElementById('buddhist-value').textContent = `${gregorianDate.split(',')[0]}, ${date.getFullYear() + 543} BE`;
}

// Era Finder Functionality
const findEraBtn = document.getElementById('find-era-btn');
findEraBtn.addEventListener('click', findEra);

function findEra() {
    const yearInput = document.getElementById('year-input').value;
    const eraType = document.getElementById('era-type').value;
    const region = document.getElementById('region').value;
    const errorElement = document.getElementById('era-error');
    if (!yearInput) {
        errorElement.style.display = 'block';
        return;
    }
    errorElement.style.display = 'none';
    let year = parseInt(yearInput);
    // Convert BCE/BC to negative years
    if (eraType === 'bce') {
        year = -year;
    }
    // Very simplified era determination
    let primaryEra, subEra, contemporaryEras;
    if (year < -3000) {
        primaryEra = "Prehistoric Era";
        subEra = "Stone Age";
        contemporaryEras = "Paleolithic Period, Early Human Development";
    } else if (year < -1200) {
        primaryEra = "Ancient Era";
        subEra = "Bronze Age";
        contemporaryEras = "Early Civilizations, Ancient Egypt, Mesopotamia";
    } else if (year < -500) {
        primaryEra = "Ancient Era";
        subEra = "Iron Age";
        contemporaryEras = "Classical Greece, Zhou Dynasty, Early Rome";
    } else if (year < 500) {
        primaryEra = "Classical Era";
        subEra = "Roman Period";
        contemporaryEras = "Han Dynasty, Gupta Empire, Late Antiquity";
    } else if (year < 1000) {
        primaryEra = "Medieval Era";
        subEra = "Early Middle Ages";
        contemporaryEras = "Byzantine Empire, Islamic Golden Age, Tang Dynasty";
    } else if (year < 1500) {
        primaryEra = "Medieval Era";
        subEra = "High/Late Middle Ages";
        contemporaryEras = "Crusades, Mongol Empire, Renaissance Beginnings";
    } else if (year < 1800) {
        primaryEra = "Early Modern Era";
        subEra = "Renaissance and Enlightenment";
        contemporaryEras = "Age of Discovery, Reformation, Scientific Revolution";
    } else if (year < 1900) {
        primaryEra = "Modern Era";
        subEra = "Industrial Age";
        contemporaryEras = "Victorian Era, Imperialism, Nationalism";
    } else if (year < 1950) {
        primaryEra = "Modern Era";
        subEra = "World Wars Period";
        contemporaryEras = "Interwar Period, Great Depression, Modernism";
    } else if (year < 1990) {
        primaryEra = "Modern Era";
        subEra = "Cold War Era";
        contemporaryEras = "Space Age, Decolonization, Atomic Age";
    } else {
        primaryEra = "Contemporary Era";
        subEra = "Information Age";
        contemporaryEras = "Digital Revolution, Globalization, Post-Cold War";
    }
    // Update result view
    document.getElementById('primary-era').textContent = primaryEra;
    document.getElementById('sub-era').textContent = subEra;
    document.getElementById('contemporary-eras').textContent = contemporaryEras;
}

// Age Calculator Functionality
const calculateAgeBtn = document.getElementById('calculate-age-btn');
calculateAgeBtn.addEventListener('click', calculateAge);

function calculateAge() {
    const birthDateInput = document.getElementById('birth-date').value;
    const calculationType = document.getElementById('calculation-date-type').value;
    const errorElement = document.getElementById('age-error');
    if (!birthDateInput) {
        errorElement.style.display = 'block';
        return;
    }
    errorElement.style.display = 'none';
    const birthDate = new Date(birthDateInput);
    let calculationDate;
    if (calculationType === 'today') {
        calculationDate = new Date();
    } else {
        const specificDateInput = document.getElementById('specific-date').value;
        if (!specificDateInput) {
            errorElement.style.display = 'block';
            return;
        }
        calculationDate = new Date(specificDateInput);
    }
    // Calculate age
    let ageYears = calculationDate.getFullYear() - birthDate.getFullYear();
    let ageMonths = calculationDate.getMonth() - birthDate.getMonth();
    let ageDays = calculationDate.getDate() - birthDate.getDate();
    // Adjust for negative months or days
    if (ageDays < 0) {
        ageMonths--;
        // Get days in the previous month
        const prevMonthDate = new Date(calculationDate.getFullYear(), calculationDate.getMonth(), 0);
        ageDays += prevMonthDate.getDate();
    }
    if (ageMonths < 0) {
        ageYears--;
        ageMonths += 12;
    }
    // Calculate total days
    const timeDiff = Math.abs(calculationDate - birthDate);
    const totalDays = Math.floor(timeDiff / (1000 * 60 * 60 * 24));
    // Determine birth era
    let birthEra;
    const birthYear = birthDate.getFullYear();
    if (birthYear < 1900) {
        birthEra = "Industrial Age";
    } else if (birthYear < 1950) {
        birthEra = "World Wars Period";
    } else if (birthYear < 1990) {
        birthEra = "Cold War Era";
    } else {
        birthEra = "Information Age";
    }
    // Update result view
    document.getElementById('age-years').textContent = `${ageYears} years, ${ageMonths} months, ${ageDays} days`;
    document.getElementById('age-days').textContent = `${totalDays.toLocaleString()} days`;
    document.getElementById('birth-era').textContent = birthEra;
}

// Timeline Filtering Functionality
const eraFilter = document.getElementById('era-filter');
eraFilter.addEventListener('change', filterTimeline);

function filterTimeline() {
    const selectedRegion = eraFilter.value;
    // In a real implementation, this would filter actual data
    // For this demonstration, we'll just simulate filtering
    const allEraItems = document.querySelectorAll('.era-era-item');
    if (selectedRegion === 'all') {
        allEraItems.forEach(item => item.style.display = 'block');
        return;
    }
    // Simple filter simulation
    allEraItems.forEach((item, index) => {
        // Show or hide items based on a pattern for demonstration
        // In a real implementation, each item would have region data
        if (index % 3 === 0 && selectedRegion === 'europe') {
            item.style.display = 'none';
        } else if (index % 3 === 1 && selectedRegion === 'asia') {
            item.style.display = 'none';
        } else if (index % 3 === 2 && selectedRegion === 'america') {
            item.style.display = 'none';
        } else if (index % 2 === 0 && selectedRegion === 'africa') {
            item.style.display = 'none';
        } else if (index % 2 === 1 && selectedRegion === 'middle-east') {
            item.style.display = 'none';
        } else {
            item.style.display = 'block';
        }
    });
}

// Initialize date fields with default values
document.addEventListener('DOMContentLoaded', () => {
    // Set today's date as default for date input
    const today = new Date();
    const formattedDate = today.toISOString().split('T')[0];
    document.getElementById('date-input').value = formattedDate;
    document.getElementById('birth-date').value = formattedDate;
    document.getElementById('specific-date').value = formattedDate;
     // Initialize with starting values
    convertDate();
});
</script>
</body>
</html>
