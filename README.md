<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jaelin Whitt - Strategic Account Manager</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- React & ReactDOM -->
    <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    
    <!-- Babel for JSX -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <style>
        /* Custom Scrollbar for a sleek look */
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: transparent;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background-color: #cbd5e1;
            border-radius: 20px;
        }
        body {
            margin: 0;
            padding: 0;
            background-color: #F8FAFC;
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect } = React;
        
        // Define Icon components using raw Lucide SVG paths
        // This avoids the lucide-react import error in the standalone HTML version
        const IconWrapper = ({ children, size = 24, className = "" }) => (
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            width={size} 
            height={size} 
            viewBox="0 0 24 24" 
            fill="none" 
            stroke="currentColor" 
            strokeWidth="2" 
            strokeLinecap="round" 
            strokeLinejoin="round" 
            className={className}
          >
            {children}
          </svg>
        );

        const User = (props) => <IconWrapper {...props}><path d="M19 21v-2a4 4 0 0 0-4-4H9a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></IconWrapper>;
        const Award = (props) => <IconWrapper {...props}><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89 17 22l-5-3-5 3 1.523-9.11"/></IconWrapper>;
        const ShieldCheck = (props) => <IconWrapper {...props}><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="m9 12 2 2 4-4"/></IconWrapper>;
        const Cpu = (props) => <IconWrapper {...props}><rect x="4" y="4" width="16" height="16" rx="2" ry="2"/><rect x="9" y="9" width="6" height="6"/><line x1="9" y1="1" x2="9" y2="4"/><line x1="15" y1="1" x2="15" y2="4"/><line x1="9" y1="20" x2="9" y2="23"/><line x1="15" y1="20" x2="15" y2="23"/><line x1="20" y1="9" x2="23" y2="9"/><line x1="20" y1="14" x2="23" y2="14"/><line x1="1" y1="9" x2="4" y2="9"/><line x1="1" y1="14" x2="4" y2="14"/></IconWrapper>;
        const Heart = (props) => <IconWrapper {...props}><path d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.3 1.5 4.05 3 5.5l7 7Z"/></IconWrapper>;
        const Home = (props) => <IconWrapper {...props}><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></IconWrapper>;
        const GraduationCap = (props) => <IconWrapper {...props}><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></IconWrapper>;
        const Briefcase = (props) => <IconWrapper {...props}><rect x="2" y="7" width="20" height="14" rx="2" ry="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/></IconWrapper>;
        const Users = (props) => <IconWrapper {...props}><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></IconWrapper>;
        const MessageSquare = (props) => <IconWrapper {...props}><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></IconWrapper>;
        const ChevronLeft = (props) => <IconWrapper {...props}><polyline points="15 18 9 12 15 6"/></IconWrapper>;
        const ChevronRight = (props) => <IconWrapper {...props}><polyline points="9 18 15 12 9 6"/></IconWrapper>;
        const ThumbsUp = (props) => <IconWrapper {...props}><path d="M7 10v12"/><path d="M15 5.88 14 10h5.83a2 2 0 0 1 1.92 2.56l-2.33 8A2 2 0 0 1 17.5 22H4a2 2 0 0 1-2-2v-8a2 2 0 0 1 2-2h2.76a2 2 0 0 0 1.79-1.11L12 2h0a3.13 3.13 0 0 1 3 3.88Z"/></IconWrapper>;
        const Lightbulb = (props) => <IconWrapper {...props}><path d="M15 14c.2-1 .7-1.7 1.5-2.5 1-.9 1.5-2.2 1.5-3.5A6 6 0 0 0 6 8c0 1 .2 2.2 1.5 3.5.7.9 1.2 1.5 1.5 2.5"/><path d="M9 18h6"/><path d="M10 22h4"/></IconWrapper>;
        const Building2 = (props) => <IconWrapper {...props}><path d="M6 22V4a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v18Z"/><path d="M6 12H4a2 2 0 0 0-2 2v6a2 2 0 0 0 2 2h2"/><path d="M18 9h2a2 2 0 0 1 2 2v9a2 2 0 0 1-2 2h-2"/><path d="M10 6h4"/><path d="M10 10h4"/><path d="M10 14h4"/><path d="M10 18h4"/></IconWrapper>;
        const Globe = (props) => <IconWrapper {...props}><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></IconWrapper>;
        const TrendingUp = (props) => <IconWrapper {...props}><polyline points="22 7 13.5 15.5 8.5 10.5 2 17"/><polyline points="16 7 22 7 22 13"/></IconWrapper>;
        const Target = (props) => <IconWrapper {...props}><circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="6"/><circle cx="12" cy="12" r="2"/></IconWrapper>;
        const Terminal = (props) => <IconWrapper {...props}><polyline points="4 17 10 11 4 5"/><line x1="12" y1="19" x2="20" y2="19"/></IconWrapper>;
        const Database = (props) => <IconWrapper {...props}><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></IconWrapper>;
        const CheckCircle2 = (props) => <IconWrapper {...props}><circle cx="12" cy="12" r="10"/><path d="m9 12 2 2 4-4"/></IconWrapper>;
        const Zap = (props) => <IconWrapper {...props}><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></IconWrapper>;

        const App = () => {
          const [currentPage, setCurrentPage] = useState(0);
          const [selectedQuestion, setSelectedQuestion] = useState(0);
          const [displayText, setDisplayText] = useState("");
          const [isTyping, setIsTyping] = useState(false);
          const [isProcessing, setIsProcessing] = useState(false);
          const [latency, setLatency] = useState(12);
          const [hoveredTag, setHoveredTag] = useState(null);

          const questions = [
            { id: 0, icon: <Terminal size={16} />, q: "Who is Jaelin?", a: "I'm a lifelong Atlanta native, a strategic Account Manager, and a Salesforce Certified Administrator. I've spent the last six years mastering B2B relationship management and CRM automation. On a personal note, I’m a proud husband and a new homeowner. I’m looking for a long-term corporate 'home' where I can drive retention, scale processes, and make an immediate impact on your bottom line." },
            { id: 1, icon: <TrendingUp size={16} />, q: "How do I benefit your organization?", a: "I bring immediate ROI to your company in three distinct ways. First, I protect and expand revenue—I maintain an 89% gross retention rate and drive a 115% Net Revenue Retention (NRR) through strategic cross-selling. Second, I scale efficiency—I build Salesforce automations that save teams 10+ hours a week. Third, I am a culture-add. I treat your clients' KPIs as my own, and I am deeply committed to lifting up my peers and growing with your organization long-term." },
            { id: 2, icon: <Globe size={16} />, q: "Jonell P.R. Impact?", a: "At Jonell P.R. Brand Management, I manage a $2.8M enterprise portfolio. I specialize in high-touch lifecycle management and heavy cross-functional collaboration, aligning product, sales, and support to facilitate impactful QBRs. It's all about cultivating deep loyalty and ensuring the client sees me as a strategic partner, which naturally opens the door for cross-selling and account expansion." },
            { id: 3, icon: <Database size={16} />, q: "Process Scalability?", a: "I believe in being proactive, not reactive. At Jonell P.R., I built automated 30/60/90-day review checkpoints using Zapier and Salesforce to catch account health issues early. This proactive approach reduced client escalations by 42% and protected $2.6 Million in ARR across 32 enterprise accounts. I build systems that allow a business to scale smoothly." },
            { id: 4, icon: <Cpu size={16} />, q: "Salesforce Edge?", a: "I realized early on that being great with clients isn't enough; you need to master the systems that support them. I became a Salesforce Certified Administrator so I could build automated workflows and health dashboards. For my team, these automations saved us over 10 hours a week, freeing us up for high-value, strategic conversations with our partners." },
            { id: 5, icon: <Users size={16} />, q: "Team Leadership?", a: "Managing a team is all about clear communication and standardizing success. I built a custom onboarding playbook in Salesforce that cut new-hire ramp time by 30%. But my proudest leadership moment is my 1:1 coaching—I've mentored sales associates who were on Performance Improvement Plans (PIPs) and successfully coached them into becoming top 10% performers for our entire district." },
            { id: 6, icon: <ShieldCheck size={16} />, q: "Churn Management?", a: "I hate losing accounts. My philosophy is that churn is usually a symptom of poor onboarding or missed signals. By managing custom Salesforce account health dashboards, I reduced response times to 'at-risk' signals from weeks to days. That visibility allowed for earlier interventions, which directly supported a 19% churn reduction across my book of business." },
            { id: 7, icon: <Zap size={16} />, q: "AI in your workflow?", a: "I'm currently finalizing my Agentforce AI Specialist certification. I love using AI practically—like analyzing customer adoption metrics to predict churn or automating workflow drafts. It’s not about replacing the human element; it’s about freeing up my schedule so I can focus on actual, consultative relationship-building with key stakeholders." },
            { id: 8, icon: <Building2 size={16} />, q: "Mattress Firm Exp?", a: "My time as a Senior Store Manager at Mattress Firm deeply honed my sales proficiency and emotional intelligence. I managed complex customer disputes across multiple locations while consistently driving revenue. I hit 163% to quota and grew my portfolio revenue by 23% YoY through consultative cross-selling. It taught me how to de-escalate situations while simultaneously identifying expansion opportunities." },
            { id: 9, icon: <MessageSquare size={16} />, q: "Client Relationships?", a: "I use a highly consultative approach. I never want to just sell a renewal; I want to solve a core business problem. By doing deep discovery, I naturally uncover cross-selling opportunities that genuinely benefit the client. This approach of tying our SLA deliverables directly to their core KPIs is exactly how I achieve that 115% net revenue retention." },
            { id: 10, icon: <Target size={16} />, q: "Pipeline Generation?", a: "Account Management isn't just defense; it's also about identifying expansion signals. During my time as an SDR, I accomplished $1.3 Million in new pipeline generation. I standardized high-intent lead handoffs through cross-functional collaboration with Account Executives and C-suite stakeholders. I always keep my eyes open for cross-sell opportunities to maximize account value." },
            { id: 11, icon: <Cpu size={16} />, q: "Time Management?", a: "With a busy portfolio, I live by the Eisenhower Matrix to prioritize my day. But my real secret is workflow automation. If a task is repetitive, I build a Zapier or Salesforce flow for it. That ensures my 'human' hours are spent on strategic account planning, QBR facilitation, and coaching, not doing manual data entry." },
            { id: 12, icon: <Award size={16} />, q: "De-escalation?", a: "Whenever a conflict arises, people just want to be heard. I learned that by pairing active listening with a proactive framework, you can turn a frustrated client into a loyal advocate. You have to stay calm, rely on the contract data, be fair, and constantly look for the win-win scenario that protects the company." },
            { id: 13, icon: <Home size={16} />, q: "Personal Stability?", a: "I'm in a really great place personally. I got married in February 2026 and we recently bought a home here in Atlanta. Because I'm so rooted now, I’m not looking to job-hop. I’m genuinely looking for a long-term corporate 'home' where I can invest my time, grow my skills, and build a lasting legacy with one amazing team." },
            { id: 14, icon: <GraduationCap size={16} />, q: "Dealing with metrics?", a: "I'm extremely data-driven. I was ranked #1 nationally for Team Finance Applications and was named 'Closer of the Year' twice. But honestly, those numbers just reflect consistency. If you take care of the daily inputs—like pipeline hygiene, prompt SLA responses, and proactive health scoring—the big metrics take care of themselves." },
            { id: 15, icon: <Heart size={16} />, q: "Hobbies & Work Ethic?", a: "I absolutely love baking pastries from scratch. It sounds funny, but baking is a lot like account management—you need patience, precise measurements, and you have to follow the process to get a great result. I’m also a big sports fan and love spending time at home with my Cane Corso." },
            { id: 16, icon: <ShieldCheck size={16} />, q: "What are your values?", a: "Integrity, honesty, and hard work are my core drivers. I really value fairness and putting people first. I try to be the kind of colleague who is accommodating and willing to step up, but also focused enough to politely push back when we need to protect the company's ARR and operational boundaries." },
            { id: 17, icon: <MessageSquare size={16} />, q: "Public Speaking?", a: "It used to terrify me! But over time, I pushed myself to get better. Now, I’m very comfortable presenting, whether it's leading an executive QBR or speaking to a larger audience. I try to keep it authentic, data-backed, and focused on collective goals without sounding over-rehearsed." },
            { id: 18, icon: <Users size={16} />, q: "Team Coaching?", a: "I take a lot of pride in coaching others. I conduct regular 1:1 sessions and review checkpoints to help my peers or direct reports remove roadblocks. I view feedback as a gift that helps us all elevate the customer experience and hit our departmental KPIs." },
            { id: 19, icon: <Briefcase size={16} />, q: "Company Fit?", a: "I want to work somewhere that values innovation, celebrates hard work, and supports long-term growth. I’m a very giving person and a dedicated employee, so finding a culture that feels collaborative, trusting, and forward-thinking is really important to me. If we align on those values, I will be a major asset to your team." }
          ];

          const metadataDefinitions = [
            { id: 'roi', keywords: ['roi', 'benefit', 'bottom line'], icon: TrendingUp, color: 'text-amber-500', bg: 'bg-amber-50/80', border: 'border-amber-200/50', title: 'Return on Investment', bullets: ['89% Gross Retention Rate', '115% Net Revenue Retention (NRR)', '$2.6M ARR Protected'] },
            { id: 'sales', keywords: ['cross-sell', 'quota', 'sales proficiency', 'performance improvement plan'], icon: Target, color: 'text-orange-500', bg: 'bg-orange-50/80', border: 'border-orange-200/50', title: 'Sales Metrics', bullets: ['163% to Quota Achievement', '$1.3M Pipeline Generation', 'Coached PIP to Top 10%'] },
            { id: 'crm', keywords: ['salesforce', 'zapier'], icon: Cpu, color: 'text-blue-500', bg: 'bg-blue-50/80', border: 'border-blue-200/50', title: 'CRM Architecture', bullets: ['Salesforce Certified Admin', 'Automated Zapier Workflows', '10+ Hours/Week Recovered'] },
            { id: 'leadership', keywords: ['team', 'coach', 'culture', 'cross-functional'], icon: Users, color: 'text-emerald-500', bg: 'bg-emerald-50/80', border: 'border-emerald-200/50', title: 'Cross-Functional Leadership', bullets: ['Led 12-person Associates Team', '30% Faster Onboarding Time', 'C-Suite Stakeholder Alignment'] },
            { id: 'portfolio', keywords: ['client', 'retention', 'arr', 'portfolio'], icon: Database, color: 'text-purple-500', bg: 'bg-purple-50/80', border: 'border-purple-200/50', title: 'Enterprise Portfolio', bullets: ['$2.8M Book of Business', '32 Enterprise Key Accounts', 'SLA & QBR Facilitation'] },
            { id: 'stable', keywords: ['homeowner', 'married', 'long-term'], icon: Heart, color: 'text-rose-500', bg: 'bg-rose-50/80', border: 'border-rose-200/50', title: 'Rooted & Stable', bullets: ['Atlanta Native & Homeowner', 'Married in February 2026', 'Seeking 10+ Year Career Home'] }
          ];

          const questionsPerPage = 3;
          const totalPages = Math.ceil(questions.length / questionsPerPage);
          const currentQuestions = questions.slice(currentPage * questionsPerPage, (currentPage + 1) * questionsPerPage);

          const currentAnswer = questions[selectedQuestion].a.toLowerCase();
          const activeTags = metadataDefinitions.filter(tag => tag.keywords.some(kw => currentAnswer.includes(kw)));

          useEffect(() => {
            let isCancelled = false; 
            let bufferTimeout;
            let typeTimeout;

            setIsProcessing(true);
            setIsTyping(false);
            setDisplayText("");
            setHoveredTag(null);
            
            const simulatedLatency = Math.floor(Math.random() * 150) + 150;
            setLatency(simulatedLatency);

            bufferTimeout = setTimeout(() => {
              if (isCancelled) return;
              
              setIsProcessing(false);
              setIsTyping(true);
              let index = 0;
              const fullText = questions[selectedQuestion].a;
              
              const typeNextChar = () => {
                if (isCancelled) return;
                
                if (index <= fullText.length) {
                  setDisplayText(fullText.slice(0, index));
                  index++;
                  const nextDelay = Math.random() * 10 + 5; 
                  typeTimeout = setTimeout(typeNextChar, nextDelay);
                } else {
                  setIsTyping(false);
                }
              };
              
              typeNextChar();
            }, simulatedLatency);

            return () => {
              isCancelled = true;
              clearTimeout(bufferTimeout);
              clearTimeout(typeTimeout);
            };
          }, [selectedQuestion]);

          return (
            <div className="flex flex-col h-screen bg-[#F8FAFC] font-sans text-slate-800 relative overflow-hidden">
              <div className="absolute inset-0 z-0 pointer-events-none overflow-hidden">
                <div className="absolute inset-0 opacity-[0.15]" style={{ backgroundImage: 'radial-gradient(#64748b 1px, transparent 1px)', backgroundSize: '24px 24px' }}></div>
                <div className="absolute -top-40 -left-40 w-96 h-96 bg-blue-400 rounded-full mix-blend-multiply filter blur-[128px] opacity-30 animate-pulse"></div>
                <div className="absolute top-40 -right-20 w-80 h-80 bg-emerald-400 rounded-full mix-blend-multiply filter blur-[128px] opacity-20"></div>
                <div className="absolute -bottom-40 left-1/2 w-96 h-96 bg-indigo-400 rounded-full mix-blend-multiply filter blur-[128px] opacity-20"></div>
              </div>

              <header className="h-14 bg-slate-900/95 backdrop-blur-md border-b border-slate-800/80 flex items-center px-6 justify-between shrink-0 shadow-[0_4px_30px_rgba(0,0,0,0.1)] z-20">
                <div className="flex items-center space-x-3">
                  <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-blue-500 to-indigo-600 flex items-center justify-center shadow-inner border border-white/10">
                    <ThumbsUp size={16} className="text-white drop-shadow-md" />
                  </div>
                  <div className="flex flex-col">
                    <h1 className="text-sm font-bold text-white tracking-wide leading-none">JAELIN_WHITT_OS //</h1>
                    <p className="text-[9px] text-blue-400 font-mono uppercase tracking-widest mt-0.5 opacity-90">Technical Account Manager Profile</p>
                  </div>
                </div>
                <div className="flex items-center space-x-4">
                  <div className="hidden md:flex items-center space-x-3 bg-slate-800/80 px-3 py-1.5 rounded-md border border-slate-700/50 shadow-inner">
                    <div className="w-2 h-2 rounded-full bg-emerald-400 animate-pulse shadow-[0_0_10px_rgba(52,211,153,0.8)]"></div>
                    <span className="text-[10px] font-mono text-emerald-100 uppercase tracking-wider opacity-90">Status: Verified & Ready</span>
                  </div>
                </div>
              </header>

              <main className="flex-1 overflow-y-auto p-4 md:p-8 flex flex-col items-center custom-scrollbar scroll-smooth relative z-10">
                <div className="w-full max-w-4xl space-y-6 mt-4 pb-32">
                  <div className="flex justify-end animate-[fadeIn_0.5s_ease-out]">
                    <div className="bg-white/80 backdrop-blur-sm border border-slate-200/60 text-slate-700 p-3.5 px-5 rounded-2xl shadow-sm max-w-[80%] flex items-center gap-3 font-mono text-xs">
                      <span className="text-slate-400">&gt; query --execute</span>
                      <span className="font-bold text-indigo-600">"{questions[selectedQuestion].q}"</span>
                    </div>
                  </div>

                  <div className="flex justify-start">
                    <div className="bg-white/90 backdrop-blur-xl rounded-2xl shadow-[0_8px_30px_rgb(0,0,0,0.04)] border border-white w-full min-h-[360px] relative transition-all duration-300 overflow-visible flex flex-col">
                      <div className="h-9 bg-slate-50/50 border-b border-slate-200/60 rounded-t-2xl flex items-center justify-between px-5 shrink-0">
                        <div className="flex items-center space-x-2.5">
                          <div className="w-2.5 h-2.5 rounded-full bg-rose-400 shadow-sm border border-rose-500/20"></div>
                          <div className="w-2.5 h-2.5 rounded-full bg-amber-400 shadow-sm border border-amber-500/20"></div>
                          <div className="w-2.5 h-2.5 rounded-full bg-emerald-400 shadow-sm border border-emerald-500/20"></div>
                        </div>
                        <div className="flex items-center space-x-4 font-mono text-[9px] text-slate-400 uppercase tracking-widest">
                          <span className="flex items-center gap-1.5"><CheckCircle2 size={11} className="text-emerald-500" /> 200 OK</span>
                          <span className="opacity-70">Lat: {isProcessing ? '--' : `${latency}ms`}</span>
                        </div>
                      </div>

                      <div className="p-8 md:p-10 flex-1 flex flex-col relative z-10">
                        <div className="flex items-center space-x-2.5 mb-7">
                          <div className="bg-indigo-50 p-1.5 rounded-md border border-indigo-100">
                            <Lightbulb size={14} className="text-indigo-600 drop-shadow-sm" />
                          </div>
                          <span className="text-[10px] font-mono font-bold uppercase tracking-[0.15em] text-indigo-600/80">
                             [ Execution Output ]
                          </span>
                        </div>
                        
                        {isProcessing ? (
                          <div className="flex items-center space-x-3 text-slate-400 font-mono text-sm h-full flex-1">
                            <Zap size={16} className="animate-pulse text-amber-500" />
                            <span className="animate-pulse tracking-wide">Retrieving strategic data points...</span>
                          </div>
                        ) : (
                          <p className="text-lg md:text-[22px] text-slate-700 leading-[1.7] font-medium tracking-tight">
                            {displayText}
                            {isTyping && <span className="inline-block w-2.5 h-5 ml-1.5 -mb-0.5 bg-indigo-500 animate-[pulse_0.8s_cubic-bezier(0.4,0,0.6,1)_infinite] shadow-[0_0_8px_rgba(99,102,241,0.6)] rounded-sm" />}
                          </p>
                        )}

                        {!isTyping && !isProcessing && activeTags.length > 0 && (
                          <div className="mt-auto pt-8 border-t border-slate-100/80 flex flex-wrap gap-2.5 relative z-50">
                            {activeTags.map((tag) => (
                              <div 
                                key={tag.id} 
                                className="relative cursor-help"
                                onMouseEnter={() => setHoveredTag(tag.id)}
                                onMouseLeave={() => setHoveredTag(null)}
                              >
                                <div className={`${tag.bg} ${tag.border} px-3.5 py-2 rounded-lg border flex items-center space-x-2 transition-all duration-300 ${hoveredTag === tag.id ? 'shadow-md scale-105' : ''}`}>
                                  <tag.icon size={13} className={`${tag.color} drop-shadow-sm`} />
                                  <span className="text-[10px] font-mono font-bold text-slate-700 uppercase tracking-wider">{tag.title}</span>
                                </div>
                                
                                <div className={`absolute top-full left-1/2 transform -translate-x-1/2 mt-3 w-56 transition-all duration-200 z-[100] origin-top ${hoveredTag === tag.id ? 'opacity-100 scale-100 pointer-events-auto' : 'opacity-0 scale-95 pointer-events-none'}`}>
                                  <div className="bg-slate-900/95 backdrop-blur-xl rounded-xl shadow-[0_10px_40px_rgba(0,0,0,0.3)] border border-slate-700 p-4 relative">
                                     <div className="absolute -top-1.5 left-1/2 transform -translate-x-1/2 w-3 h-3 bg-slate-900/95 border-t border-l border-slate-700 rotate-45"></div>
                                     <h4 className="text-white font-mono text-[10px] uppercase tracking-widest font-bold mb-3 border-b border-slate-700 pb-2 relative z-10">{tag.title} Insights</h4>
                                     <ul className="space-y-2.5 relative z-10">
                                       {tag.bullets.map((bullet, idx) => (
                                          <li key={idx} className="flex items-start text-[11px] text-slate-300 leading-snug">
                                             <span className={`mr-2 font-bold ${tag.color}`}>▹</span>
                                             <span>{bullet}</span>
                                          </li>
                                       ))}
                                     </ul>
                                  </div>
                                </div>
                              </div>
                            ))}
                          </div>
                        )}
                      </div>
                    </div>
                  </div>
                </div>
              </main>

              <footer className="shrink-0 bg-white/80 backdrop-blur-xl border-t border-slate-200/60 p-5 flex flex-col items-center shadow-[0_-10px_40px_rgba(0,0,0,0.03)] z-30 relative">
                <div className="w-full max-w-4xl flex items-center space-x-4">
                  <button 
                    onClick={() => {
                      if (isProcessing) return; 
                      const prev = (currentPage - 1 + totalPages) % totalPages;
                      setCurrentPage(prev);
                    }}
                    className="p-3 bg-white hover:bg-slate-50 border border-slate-200/80 rounded-xl transition-all active:scale-95 text-slate-400 hover:text-indigo-600 shadow-sm"
                  >
                    <ChevronLeft size={18} />
                  </button>

                  <div className="flex-1 grid grid-cols-3 gap-3">
                    {currentQuestions.map((item) => (
                      <button
                        key={item.id}
                        onClick={() => {
                          if (selectedQuestion !== item.id) setSelectedQuestion(item.id);
                        }}
                        className={`group px-3 py-3 rounded-xl border transition-all duration-300 flex flex-col items-center justify-center space-y-2 text-center overflow-hidden relative ${
                          selectedQuestion === item.id 
                          ? 'bg-slate-900 border-slate-800 text-white shadow-[0_4px_15px_rgba(0,0,0,0.15)] scale-[1.02]' 
                          : 'bg-white border-slate-200/80 text-slate-600 hover:border-indigo-300 hover:shadow-md'
                        }`}
                      >
                        {selectedQuestion === item.id && (
                          <div className="absolute top-0 left-0 w-full h-0.5 bg-gradient-to-r from-blue-500 to-indigo-500"></div>
                        )}
                        <div className={`transition-transform duration-300 group-hover:scale-110 ${selectedQuestion === item.id ? 'text-indigo-400' : 'text-slate-400 group-hover:text-indigo-500'}`}>
                          {React.cloneElement(item.icon, { size: 16 })}
                        </div>
                        <span className="text-[10px] font-mono font-bold uppercase tracking-tight">{item.q}</span>
                      </button>
                    ))}
                  </div>

                  <button 
                    onClick={() => {
                      if (isProcessing) return; 
                      const next = (currentPage + 1) % totalPages;
                      setCurrentPage(next);
                    }}
                    className="p-3 bg-white hover:bg-slate-50 border border-slate-200/80 rounded-xl transition-all active:scale-95 text-slate-400 hover:text-indigo-600 shadow-sm"
                  >
                    <ChevronRight size={18} />
                  </button>
                </div>
                
                <div className="mt-4 flex items-center justify-between w-full max-w-4xl px-4">
                   <span className="text-[9px] font-mono text-slate-400 uppercase tracking-widest">&gt; Select execution module to retrieve data</span>
                   <div className="flex space-x-1.5">
                     {[...Array(totalPages)].map((_, i) => (
                       <div key={i} className={`w-1.5 h-1.5 rounded-full transition-all duration-300 ${i === currentPage ? 'bg-indigo-500 w-4 shadow-[0_0_8px_rgba(99,102,241,0.6)]' : 'bg-slate-300'}`} />
                     ))}
                   </div>
                </div>
              </footer>
            </div>
          );
        };

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
