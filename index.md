<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEXEO Interactive Linear Release Path</title>
    
<script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* --- Updated Tab Button Styles (Kept for active/inactive logic in JS, even if buttons are hidden) --- */
        .tab-btn {
            /* Base button styling: pill shape, spacing, transition, small shadow */
            @apply px-5 py-2 mx-1 my-1 text-sm md:text-base font-semibold rounded-full transition-colors duration-200 shadow-md;
            /* Hide the actual buttons, but they still exist in the DOM for JS targeting */
            display: none;
        }
        .active-tab {
            /* Active button: solid indigo background, white text, enhanced shadow */
            @apply bg-indigo-600 text-white shadow-indigo-400/70;
        }
        .inactive-tab {
            /* Inactive button: light slate background, slate text, hover effect */
            @apply bg-slate-200 text-slate-700 hover:bg-indigo-100 hover:text-indigo-700;
        }
        /* --- Linear Timeline Styles --- */
        .linear-timeline {
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            padding: 2rem 0;
            margin: 0 auto;
            max-width: 900px;
        }
        .linear-timeline::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 4px;
            background-color: #cbd5e1; /* slate-300 */
            transform: translateY(-50%);
            z-index: 0;
        }
        .timeline-step {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            position: relative;
            z-index: 1;
            cursor: pointer;
            transition: transform 0.2s ease-in-out, background-color 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
            border-radius: 0.5rem; /* rounded-lg */
            padding: 0.5rem;
            margin: 0 0.25rem; /* Small margin between steps */
        }
        .timeline-step:hover {
            transform: translateY(-5px);
            background-color: #e2e8f0; /* slate-200 */
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1); /* shadow-md */
        }
        .timeline-step.active-step .timeline-icon-wrapper {
            background-color: #4f46e5; /* indigo-600 */
            box-shadow: 0 0 0 4px rgba(79, 70, 229, 0.4); /* Focus ring effect */
        }
        .timeline-step.active-step .timeline-text {
             color: #4f46e5; /* indigo-600 */
             font-weight: 700; /* Made text bolder */
        }
        .timeline-icon-wrapper {
            width: 48px; /* w-12 */
            height: 48px; /* h-12 */
            border-radius: 9999px; /* rounded-full */
            background-color: #64748b; /* slate-500 */
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 0.5rem;
            transition: background-color 0.2s ease-in-out;
        }
        .timeline-icon {
            color: #ffffff;
            font-size: 1.5rem; /* text-2xl */
        }
        .timeline-text {
            color: #475569; /* slate-600 */
            font-size: 0.875rem; /* text-sm */
            line-height: 1.25rem;
            font-weight: 500; /* Ensured text is legible */
        }
        /* Media query for smaller screens to make steps stack or wrap */
        @media (max-width: 768px) {
            .linear-timeline {
                flex-wrap: wrap;
                justify-content: space-around;
                padding: 1rem 0;
            }
            .linear-timeline::before {
                display: none; /* Hide the connecting line on smaller screens */
            }
            .timeline-step {
                flex-basis: 45%; /* Two steps per row */
                margin-bottom: 1rem;
            }
            .tab-btn {
                /* Adjust button size for mobile tabs */
                @apply px-4 py-2 text-xs;
            }
        }
        @media (max-width: 480px) {
            .timeline-step {
                flex-basis: 90%; /* One step per row */
            }
        }
    </style>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased">

    <div class="container mx-auto p-4 py-8 md:p-12 max-w-6xl">

        <header class="text-center mb-10">
            <h1 class="text-3xl md:text-4xl font-bold text-slate-900 mb-2">NEXEO Audio Platform</h1>
            <p class="text-xl md:text-2xl text-indigo-600 font-light">Controlled Upgrade & Release Path</p>
        </header>

        <section class="mb-12">
            <h2 class="text-xl font-semibold text-slate-900 mb-3 text-center">Our Release Cycle: A Linear Progression (Click to Explore)</h2>
            <p class="text-slate-700 max-w-3xl mx-auto text-center mb-6">
                Explore our step-by-step release process. Click on any phase below to see its detailed description and activities.
            </p>
            <div class="bg-white p-4 rounded-lg shadow-xl">
                <div class="linear-timeline">
                    <!-- Steps for Linear Timeline --><div id="timeline-step-1" data-target="content-1" class="timeline-step active-step">
                        <div class="timeline-icon-wrapper"><span class="timeline-icon">&#128203;</span></div>
                        <span class="timeline-text">Plan (PI)</span>
                    </div>
                    <div id="timeline-step-2" data-target="content-2" class="timeline-step">
                        <div class="timeline-icon-wrapper"><span class="timeline-icon">&#128187;</span></div>
                        <span class="timeline-text">Develop & QA</span>
                    </div>
                    <div id="timeline-step-3" data-target="content-3" class="timeline-step">
                        <div class="timeline-icon-wrapper"><span class="timeline-icon">&#128221;</span></div>
                        <span class="timeline-text">Validate & Test</span>
                    </div>
                    <div id="timeline-step-4" data-target="content-4" class="timeline-step">
                        <div class="timeline-icon-wrapper"><span class="timeline-icon">&#128374;</span></div>
                        <span class="timeline-text">Canary Rollout</span>
                    </div>
                    <div id="timeline-step-5" data-target="content-5" class="timeline-step">
                        <div class="timeline-icon-wrapper"><span class="timeline-icon">&#128640;</span></div>
                        <span class="timeline-text">Final Deploy</span>
                    </div>
                </div>
            </div>
        </section>

        <section class="bg-white p-6 md:p-8 rounded-lg shadow-xl">
            <div class="w-full">
                <!-- HIDDEN INTERACTIVE PHASE BUTTONS (kept for JS target only) --><nav class="flex flex-wrap justify-center" aria-label="Phases">
                    <button id="tab-1" data-target="content-1" class="tab-btn active-tab">
                        Plan
                    </button>
                    <button id="tab-2" data-target="content-2" class="tab-btn inactive-tab">
                        Develop
                    </button>
                    <button id="tab-3" data-target="content-3" class="tab-btn inactive-tab">
                        Validate
                    </button>
                    <button id="tab-4" data-target="content-4" class="tab-btn inactive-tab">
                        Canary
                    </button>
                    <button id="tab-5" data-target="content-5" class="tab-btn inactive-tab">
                        Deploy
                    </button>
                </nav>

                <div id="content-panels" class="py-6 md:py-8">
                    <!-- Phase 1 Content --><div id="content-1" class="tab-content">
                        <h3 class="text-2xl font-bold text-indigo-700 mb-4">Phase 1: Planning & Commitment (PI)</h3>
                        <p class="text-lg text-slate-700 mb-6">
                            The upgrade cycle begins with the Project Increment (PI) planning session. This serves as both a retrospective on past work and a concrete planning session for the upcoming quarter.
                        </p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Project Prioritization</h4>
                                    <p class="text-slate-600">We prioritize new features and enhancements, negotiate necessary resources, and solidify the scope for the next three months.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Commitment Finalization</h4>
                                    <p class="text-slate-600">All committed development items and deliverables for the upcoming quarter are finalized, establishing a clear roadmap.</p>
                                </div>
                            </li>
                        </ul>
                    </div>

                    <!-- Phase 2 Content --><div id="content-2" class="tab-content hidden">
                        <h3 class="text-2xl font-bold text-indigo-700 mb-4">Phase 2: Core Development & Continuous QA</h3>
                        <p class="text-lg text-slate-700 mb-6">
                            Following PI, the main development window for the quarter begins. This phase is characterized by feature implementation running in parallel with continuous, rigorous testing.
                        </p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Core Development</h4>
                                    <p class="text-slate-600">The majority of the quarter is dedicated to coding and integrating new features as defined during the PI planning.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Rigorous Continuous Testing</h4>
                                    <p class="text-slate-600">Every feature component undergoes continuous testing throughout the development process. Requested changes and adjustments are implemented immediately.</p>
                                </div>
                            </li>
                        </ul>
                    </div>
                    
                    <!-- Phase 3 Content --><div id="content-3" class="tab-content hidden">
                        <h3 class="text-2xl font-bold text-indigo-700 mb-4">Phase 3: Pre-Release Validation & Field Test</h3>
                        <p class="text-lg text-slate-700 mb-6">
                            Approximately two weeks before the end of the quarter, the software enters a dedicated "feature-freeze" and validation phase to stabilize the final build for release.
                        </p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Regression & Field Test</h4>
                                    <p class="text-slate-600">We enter the final, intensive regression and field test period to catch any potential issues before a wider release.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Release Candidate (RC) Generation</h4>
                                    <p class="text-slate-600">A stable Release Candidate build is generated from the fully-tested codebase.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">In-House & Local Testing</h4>
                                    <p class="text-slate-600">All functionalities are tested in-house and validated by our local active field test stores to ensure real-world compatibility.</p>
                                </div>
                            </li>
                        </ul>
                    </div>

                    <!-- Phase 4 Content --><div id="content-4" class="tab-content hidden">
                        <h3 class="text-2xl font-bold text-indigo-700 mb-4">Phase 4: Controlled Production Rollout (Canary)</h3>
                        <p class="text-lg text-slate-700 mb-6">
                            Once the Release Candidate passes all internal checks, a highly controlled, limited deployment begins to monitor performance in a live production environment.
                        </p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Canary Test Group (40+ Stores)</h4>
                                    <p class="text-slate-600">The finalized build is released to an initial group of 40+ canary stores. This serves as a final smoke and sanity test with live store activity.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Parallel Lab Release</h4>
                                    <p class="text-slate-600">Simultaneously, the build is released to brand-specific laboratories for those partners who require independent testing and approval.</p>
                                </div>
                            </li>
                        </ul>
                    </div>

                    <!-- Phase 5 Content --><div id="content-5" class="tab-content hidden">
                        <h3 class="text-2xl font-bold text-indigo-700 mb-4">Phase 5: Final Deployment & Installation</h3>
                        <p class="text-lg text-slate-700 mb-6">
                            After performance is confirmed in the canary group, the platform is rolled out to the wider customer base through a managed, approval-based process.
                        </p>
                        <ul class="space-y-4">
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Mass Rollout (Non-Approving Brands)</h4>
                                    <p class="text-slate-600">The build is rolled out to all brands that do not require external approval.</p>
                                </div>
                            </li>
                            <li id="firmware-manager-detail" class="flex flex-col cursor-pointer p-2 rounded-lg hover:bg-slate-100 transition-colors" onclick="toggleDetail('firmware-manager-info')">
                                <div class="flex items-start">
                                    <div>
                                        <h4 class="font-semibold text-slate-800">Brand Approval & Firmware Manager (Click for Detail)</h4>
                                        <p class="text-slate-600">For approving brands, HME admins use the Firmware Manager to set the installation date. This tool initiates the download post-approval.</p>
                                    </div>
                                </div>
                                <!-- Hidden detail section --><div id="firmware-manager-info" class="hidden mt-3 ml-4 md:ml-12 p-3 border-l-4 border-amber-500 bg-amber-50 text-sm text-slate-700 rounded-r-lg shadow-inner">
                                    <p class="font-bold mb-1">Role of the Firmware Manager:</p>
                                    <p>This is a critical administrative tool used by HME to ensure all devices are running the latest approved versions. It handles the scheduling of the download and installation date, providing centralized control over the deployment process.</p>
                                </div>
                            </li>
                            <li class="flex items-start">
                                <div>
                                    <h4 class="font-semibold text-slate-800">Automated Base-Side Installation</h4>
                                    <p class="text-slate-600">On the scheduled date, the base automatically downloads the software and upgrades the device based on its internal schedule.</p>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section for the first image --><section class="mt-12 text-center">
            <h2 class="text-xl font-semibold text-slate-900 mb-3">Annual Release Schedule at a Glance</h2>
            <img src="https://i.imgur.com/fCEmwqR.png" alt="Annual Release Schedule" class="mx-auto rounded-lg shadow-xl max-w-full h-auto">
        </section>

        <!-- Section for the second image --><section class="mt-8 text-center">
            <h2 class="text-xl font-semibold text-slate-900 mb-3">NEXEO Platform: Version Release Journey</h2>
            <img src="https://i.imgur.com/PVeCeMk.png" alt="Software Release Lifecycle Diagram showing a version object moving through Development, Regression Testing, Canary Testing, and Production." class="mx-auto rounded-lg shadow-xl max-w-full h-auto">
        </section>

        <footer class="text-center mt-12">
            <p class="text-sm text-slate-500">&copy; HME. All rights reserved. This document outlines a typical process and is subject to change.</p>
        </footer>

    </div>

    <script>
        function activateDetailTab(targetElement) {
            const tabs = document.querySelectorAll('.tab-btn');
            const contents = document.querySelectorAll('.tab-content');
            const targetId = targetElement.getAttribute('data-target');

            tabs.forEach(t => {
                if (t.getAttribute('data-target') === targetId) {
                    t.classList.add('active-tab');
                    t.classList.remove('inactive-tab');
                } else {
                    t.classList.remove('active-tab');
                    t.classList.add('inactive-tab');
                }
            });

            contents.forEach(content => {
                if (content.id === targetId) {
                    content.classList.remove('hidden');
                } else {
                    content.classList.add('hidden');
                }
            });

            const timelineSteps = document.querySelectorAll('.timeline-step');
            timelineSteps.forEach(step => {
                if (step.getAttribute('data-target') === targetId) {
                    step.classList.add('active-step');
                } else {
                    step.classList.remove('active-step');
                }
            });
        }

        function toggleDetail(elementId) {
            const element = document.getElementById(elementId);
            if (element) {
                element.classList.toggle('hidden');
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            const timelineSteps = document.querySelectorAll('.timeline-step');
            
            timelineSteps.forEach(step => {
                step.addEventListener('click', () => {
                    activateDetailTab(step);
                    // Removed: document.getElementById('content-panels').scrollIntoView({ behavior: 'smooth', block: 'start' });
                });
            });

            const initialStep = document.getElementById('timeline-step-1');
            if (initialStep) {
                activateDetailTab(initialStep);
            }
        });
    </script>

</body>
</html>



