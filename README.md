<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Engineering Work Request Form</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        body { 
            font-family: 'Inter', sans-serif; 
            background-color: #f1f5f9; 
            position: relative; /* Needed for the ::before pseudo-element positioning */
        }

        /* This creates a subtle watermark that does not affect the form's readability */
        body::before {
            content: "";
            position: fixed; /* Positions the watermark relative to the viewport */
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('YOUR_ICS_LOGO_URL_HERE');
            background-repeat: no-repeat;
            background-position: center center;
            background-size: 50%; /* Adjust as needed */
            opacity: 0.1; /* Adjust for desired watermark transparency */
            z-index: -1; /* Puts the watermark behind the form content */
            pointer-events: none; /* Allows clicks to pass through to the form */
        }

        .invalid-field { border-color: #ef4444; box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.2); }

        main {
            position: relative;
            z-index: 10;
            background-color: white; /* Changed to solid white for full visibility */
            padding: 2rem;
            border-radius: 2rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }

        /* These ensure form fields have a solid background and are not transparent */
        input:not([type="radio"]):not([type="checkbox"]), textarea, select {
            background-color: #ffffff;
        }
    </style>
</head>
<body class="text-slate-800">

    <main class="max-w-4xl mx-auto my-10 bg-white rounded-2xl shadow-2xl">
        <header class="text-center mb-8">
            <h1 class="text-4xl font-bold text-slate-900">Engineering Work Request (EWR)</h1>
            <p class="mt-4 text-lg text-slate-600">
                This form streamlines project requests to the engineering department.
                Please complete all fields as accurately as possible.
            </p>
        </header>

        <div id="form-status-message" class="hidden p-4 mb-6 rounded-lg text-center"></div>

        <form id="ewrForm" action="https://formsubmit.co/engineering@icstx.com" method="POST">
            
            <input type="hidden" name="_subject" value="New Engineering Work Request (EWR)">
            <input type="hidden" name="_next" value="YOUR_THANK_YOU_PAGE_URL">
            <input type="hidden" name="_captcha" value="false">

            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">A. Request Identification & Tracking</legend>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-x-6">
                        <div>
                            <label for="ewrNumber" class="block mb-2 font-medium text-slate-600">EWR Number:</label>
                            <input type="text" id="ewrNumber" name="EWR_Number" value="[Automatically Generated]" readonly class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-200 cursor-not-allowed">
                        </div>
                        <div>
                            <label for="dateOfRequest" class="block mb-2 font-medium text-slate-600">Date of Request:</label>
                            <input type="date" id="dateOfRequest" name="Date_of_Request" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                        </div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-x-6">
                        <div>
                            <label for="salespersonName" class="block mb-2 font-medium text-slate-600">Salesperson Name:</label>
                            <input type="text" id="salespersonName" name="Salesperson" placeholder="Your Full Name" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                        </div>
                        <div>
                            <label for="customerName" class="block mb-2 font-medium text-slate-600">Customer Company Name:</label>
                            <input type="text" id="customerName" name="Customer" placeholder="Customer's Company" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                        </div>
                    </div>
                </fieldset>
            </section>
            
            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">B. Project Definition</legend>
                    <div>
                        <label class="block mb-2 font-medium text-slate-600">Type of Work Requested:</label>
                        <div class="p-4 bg-slate-50 border border-slate-200 rounded-lg space-y-3">
                            <div class="flex items-center"><input type="radio" id="newProduct" name="workType" value="New Product Development" required class="mr-3 h-4 w-4 text-indigo-600 focus:ring-indigo-500"><label for="newProduct">New Product Development</label></div>
                            <div class="flex items-center"><input type="radio" id="customization" name="workType" value="Modification of an Existing Product" class="mr-3 h-4 w-4 text-indigo-600 focus:ring-indigo-500"><label for="customization">Modification of an Existing Product</label></div>
                            <div class="flex items-center"><input type="radio" id="feasibilityStudy" name="workType" value="Technical Feasibility Study" class="mr-3 h-4 w-4 text-indigo-600 focus:ring-indigo-500"><label for="feasibilityStudy">Technical Feasibility Study</label></div>
                            <div class="flex items-center"><input type="radio" id="eco" name="workType" value="Engineering Change Order (ECO)" class="mr-3 h-4 w-4 text-indigo-600 focus:ring-indigo-500"><label for="eco">Engineering Change Order (ECO)</label></div>
                            <div class="flex items-center"><input type="radio" id="techSupport" name="workType" value="Technical Support" class="mr-3 h-4 w-4 text-indigo-600 focus:ring-indigo-500"><label for="techSupport">Technical Support or Troubleshooting</label></div>
                        </div>
                    </div>
                    <div class="mt-6">
                        <label for="detailedDescription" class="block mb-2 font-medium text-slate-600">Detailed Description of Work:</label>
                        <textarea id="detailedDescription" name="Description" rows="5" placeholder="Describe the scope, objectives, and expected outcomes. What problem does this solve for the customer?" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-y"></textarea>
                    </div>
                </fieldset>
            </section>

            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">C. Technical Specifications</legend>
                    <div>
                        <label for="technicalParameters" class="block mb-2 font-medium text-slate-600">Key Technical Parameters:</label>
                        <textarea id="technicalParameters" name="Technical_Parameters" rows="4" placeholder="Include dimensions, materials, performance criteria (e.g., NEMA 1, 3R, 4X), environmental conditions, etc." class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-y"></textarea>
                    </div>
                    <div class="mt-6">
                        <label for="currentApplicationSize" class="block mb-2 font-medium text-slate-600">What is the size and current of the application?</label>
                        <textarea id="currentApplicationSize" name="Current_Application_Size" rows="3" placeholder="Specify dimensions, amperage, and other relevant details." class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-y"></textarea>
                    </div>
                    <div>
                        <label class="block mb-2 font-medium text-slate-600">Electrical Requirements:</label>
                        <div class="p-4 bg-slate-50 border border-slate-200 rounded-lg grid grid-cols-2 md:grid-cols-3 gap-3">
                            <div class="flex items-center"><input type="checkbox" id="v120_1ph3w" name="electricalReq" value="120VAC 1Ph 3-Wire" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="v120_1ph3w">120VAC 1Φ 3-Wire</label></div>
                            <div class="flex items-center"><input type="checkbox" id="v208_3ph4wY" name="electricalReq" value="208VAC 3Ph 4-Wire Wye" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="v208_3ph4wY">208VAC 3Φ 4-Wire Wye</label></div>
                            <div class="flex items-center"><input type="checkbox" id="v240_1ph3w" name="electricalReq" value="240VAC 1Ph 3-Wire" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="v240_1ph3w">240VAC 1Φ 3-Wire</label></div>
                            <div class="flex items-center"><input type="checkbox" id="v480_3ph4wY" name="electricalReq" value="480VAC 3Ph 4-Wire Wye" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="v480_3ph4wY">480VAC 3Φ 4-Wire Wye</label></div>
                            <div class="flex items-center"><input type="checkbox" id="v600_3ph4wY" name="electricalReq" value="600VAC 3Ph 4-Wire Wye" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="v600_3ph4wY">600VAC 3Φ 4-Wire Wye</label></div>
                            <div class="flex items-center"><input type="checkbox" id="otherElectrical" name="electricalReq" value="Other" class="mr-3 h-4 w-4 text-indigo-600 rounded focus:ring-indigo-500"><label for="otherElectrical">Other</label></div>
                        </div>
                        <input type="text" id="otherElectricalSpecify" name="Other_Electrical" placeholder="Specify other electrical requirements" class="hidden w-full mt-3 p-3 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                    </div>
                    <div class="mt-6">
                        <label for="complianceStandards" class="block mb-2 font-medium text-slate-600">Compliance & Standards:</label>
                        <input type="text" id="complianceStandards" name="Compliance" placeholder="e.g., UL 508A, CE, ISO, RoHS" class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                    </div>
                </fieldset>
            </section>

            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">D. Electrical System Details</legend>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-x-6">
                        <div>
                            <label for="sccrRating" class="block mb-2 font-medium text-slate-600">What is the required SCCR (Short-Circuit Current Rating)?</label>
                            <input type="text" id="sccrRating" name="SCCR_Rating" placeholder="e.g., 10kA, 65kA, 100kA" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                        </div>
                        <div>
                            <label for="sourceEntry" class="block mb-2 font-medium text-slate-600">Will the source entries be from the top or bottom?</label>
                            <select id="sourceEntry" name="Source_Entry" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                                <option value="" disabled selected>-- Select an option --</option>
                                <option value="Top">Top Entry</option>
                                <option value="Bottom">Bottom Entry</option>
                                <option value="Not Specified">Not Specified</option>
                            </select>
                        </div>
                    </div>
                    <div>
                        <label for="cableInfo" class="block mb-2 font-medium text-slate-600">Are there any indications on the wire and cable sizes?</label>
                        <textarea id="cableInfo" name="Cable_Size_Info" rows="3" placeholder="Please specify any known details about main feeder sizes, branch circuit wire gauges, etc." class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-y"></textarea>
                    </div>
                </fieldset>
            </section>

            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">E. Timeline & Urgency</legend>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-x-6">
                        <div>
                            <label for="completionDate" class="block mb-2 font-medium text-slate-600">Required Completion Date:</label>
                            <input type="date" id="completionDate" name="Required_Date" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                            <p class="text-sm text-slate-500 mt-[-8px] mb-4">Please avoid using "ASAP".</p>
                        </div>
                        <div>
                            <label for="priorityLevel" class="block mb-2 font-medium text-slate-600">Priority Level:</label>
                            <select id="priorityLevel" name="Priority" required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                                <option value="" disabled selected>-- Select a priority --</option>
                                <option value="Critical">Critical</option>
                                <option value="High">High</option>
                                <option value="Medium">Medium</option>
                                <option value="Low">Low</option>
                            </select>
                        </div>
                    </div>
                    <div>
                        <label for="priorityJustification" class="block mb-2 font-medium text-slate-600">Justification for Priority:</label>
                        <textarea id="priorityJustification" name="Justification" rows="3" placeholder="Explain why the request is 'Critical' or 'High'. e.g., risk of losing customer, contractual delivery date, etc." required class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-y"></textarea>
                    </div>
                </fieldset>
            </section>

            <section class="mb-10">
                <fieldset class="border-t-2 border-indigo-500 pt-4">
                    <legend class="text-2xl font-semibold mb-4 text-slate-800 px-2">F. Supporting Documentation & Budget</legend>
                    <div>
                        <label for="attachments" class="block mb-2 font-medium text-slate-600">Attach Files:</label>
                        <input type="file" id="attachments" name="attachment" multiple class="block w-full text-sm text-slate-500 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-indigo-50 file:text-indigo-700 hover:file:bg-indigo-100 transition">
                        <p class="text-sm text-slate-500 mt-1">You can attach customer specifications, drawings, photos, etc.</p>
                    </div>
                    <div class="mt-6">
                        <label for="budget" class="block mb-2 font-medium text-slate-600">Budget Information (Optional):</label>
                        <input type="text" id="budget" name="Budget" placeholder="e.g., Budget range, estimated project value" class="w-full p-3 mb-4 border border-slate-300 rounded-lg bg-slate-50 focus:outline-none focus:ring-2 focus:ring-indigo-500 transition">
                    </div>
                </fieldset>
            </section>

            <div class="flex flex-col md:flex-row gap-4 mt-8">
                <button type="submit" id="submit-button" class="w-full md:w-auto flex-grow py-3 px-6 bg-indigo-600 text-white font-bold rounded-lg shadow-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition disabled:bg-indigo-300 disabled:cursor-not-allowed">
                    Submit Work Request
                </button>
                <button type="reset" class="w-full md:w-auto py-3 px-6 bg-slate-200 text-slate-800 font-bold rounded-lg hover:bg-slate-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-slate-400 transition">
                    Clear Form
                </button>
            </div>
        </form>
    </main>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const form = document.getElementById('ewrForm');
            const submitButton = document.getElementById('submit-button');
            const statusMessage = document.getElementById('form-status-message');
            
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('dateOfRequest').value = today;
            
            const otherElectricalCheckbox = document.getElementById('otherElectrical');
            const otherElectricalSpecifyInput = document.getElementById('otherElectricalSpecify');
            otherElectricalCheckbox.addEventListener('change', function() {
                otherElectricalSpecifyInput.classList.toggle('hidden', !this.checked);
                if (!this.checked) { otherElectricalSpecifyInput.value = ''; }
            });

            form.addEventListener('submit', function(e) {
                clearErrors();
                if (!validateForm()) {
                    e.preventDefault();
                    showStatusMessage('Please correct the fields highlighted in red.', 'error');
                } else {
                    submitButton.disabled = true;
                    submitButton.textContent = 'Submitting...';
                }
            });

            function validateForm() {
                let isValid = true;
                const requiredFields = form.querySelectorAll('[required]');
                requiredFields.forEach(field => {
                    let isFieldValid = true;
                    if (field.type === 'radio') {
                        if (!document.querySelector(`input[name="${field.name}"]:checked`)) isFieldValid = false;
                    } else if (field.value.trim() === '') {
                        isFieldValid = false;
                    }
                    if (!isFieldValid) {
                        isValid = false;
                        const container = field.closest('.p-4') || field;
                        container.classList.add('invalid-field');
                        if (container !== field) field.classList.add('invalid-field');
                    }
                });
                return isValid;
            }

            function clearErrors() {
                form.querySelectorAll('.invalid-field').forEach(el => el.classList.remove('invalid-field'));
            }

            function showStatusMessage(message, type) {
                statusMessage.textContent = message;
                statusMessage.className = 'p-4 mb-6 rounded-lg text-center';
                if (type === 'error') {
                    statusMessage.classList.add('bg-red-100', 'text-red-800');
                }
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }
        });
    </script>
</body>
</html>
