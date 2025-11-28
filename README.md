import React, { useState, useEffect } from 'react';
import { 
  Github, 
  Linkedin, 
  Mail, 
  FileText, 
  Code, 
  Terminal, 
  Cpu, 
  Database, 
  Cloud, 
  Menu, 
  X, 
  ExternalLink,
  ChevronRight,
  Award
} from 'lucide-react';

// --- Data extracted from Resume ---
const PORTFOLIO_DATA = {
  personal: {
    name: "Sarwarish Upadhyay",
    title: "Software Engineer 2 @ Juniper Networks",
    subtitle: "Specializing in C++, Java, Microservices, and Scalable Backend Systems",
    email: "usarwarish@gmail.com",
    linkedin: "https://www.linkedin.com/in/sarwarishupadhyay",
    location: "Bengaluru, Karnataka, India",
    summary: "I am a Software Engineer skilled in Java/C++, Object-Oriented Programming and strong Computer Science fundamentals. I am an enthusiastic coder ambitious to drive innovation by solving complex technical problems. My strengths include being meticulous, quickly learning new technologies, and efficiently delivering results."
  },
  skills: {
    languages: ["Java", "C++", "Python", "JavaScript", "SQL"],
    backend: ["Spring Boot", "Node.js", "Microservices", "Multithreading", "OS Concepts"],
    frontend: ["React.js", "HTML5", "CSS3", "Tailwind"],
    devops: ["AWS", "Kubernetes", "Docker", "Git", "Jenkins", "Kafka"],
    tools: ["Jira", "UML", "VS Code", "Eclipse"]
  },
  experience: [
    {
      company: "Juniper Networks",
      role: "Software Engineer 2",
      duration: "Feb 2023 - Present",
      location: "Bengaluru",
      tech: ["C/C++", "OS", "Multithreading", "Java", "Python"],
      description: "Working on high-performance networking software. Leveraging deep knowledge of operating systems and multithreading to optimize system efficiency."
    },
    {
      company: "Tejas Networks",
      role: "Software Engineer",
      duration: "Nov 2021 - Feb 2023",
      location: "Bengaluru",
      tech: ["Java", "Python", "JS", "C/C++", "L2/L3 Switching"],
      description: "Backend development focusing on features for L2/L3 layer switches. Handled complex system integrations and feature implementation."
    },
    {
      company: "Hyland",
      role: "Software Developer",
      duration: "Sep 2021 - Nov 2021",
      location: "Kolkata",
      tech: ["Software Development", "Debugging"],
      description: "Focused on feature implementation and debugging within the core software suite."
    },
    {
      company: "Freelance",
      role: "Full Stack Developer",
      duration: "Jan 2020 - Present",
      location: "Remote",
      tech: ["Java", "Kafka", "React", "Kubernetes"],
      description: "Delivering freelance solutions using a modern stack including Java, Kafka, and Kubernetes."
    }
  ],
  internships: [
    {
      company: "The Sparks Foundation",
      role: "Web Developer Intern",
      duration: "Feb 2021 (1 Month)",
      description: "Built an exclusive Merchandise website from scratch with RazorPay payment gateway integration using React JS and Java."
    },
    {
      company: "The Sparks Foundation",
      role: "Data Science Intern",
      duration: "Nov 2020 - Jan 2021",
      description: "Conducted data analysis, created visualizations, and deployed a final presentation website using Django."
    }
  ],
  certifications: [
    "AWS Elastic Beanstalk: Deploy a Python(Flask) Web Application",
    "TI Hackathon Quarter Finalist",
    "Secure Coding in C",
    "Problem Solving (Basic)"
  ]
};

const SectionTitle = ({ title, subtitle }) => (
  <div className="mb-12 text-center">
    <h2 className="text-3xl md:text-4xl font-bold text-white mb-4 relative inline-block">
      {title}
      <span className="absolute -bottom-2 left-1/2 transform -translate-x-1/2 w-12 h-1 bg-cyan-500 rounded-full"></span>
    </h2>
    {subtitle && <p className="text-slate-400 mt-4 max-w-2xl mx-auto">{subtitle}</p>}
  </div>
);

const Card = ({ children, className = "" }) => (
  <div className={`bg-slate-800/50 backdrop-blur-sm border border-slate-700 p-6 rounded-xl hover:border-cyan-500/50 transition-all duration-300 hover:shadow-[0_0_30px_rgba(6,182,212,0.15)] ${className}`}>
    {children}
  </div>
);

const SkillTag = ({ name }) => (
  <span className="px-3 py-1 bg-slate-700/50 text-cyan-400 text-sm font-medium rounded-full border border-slate-600 hover:border-cyan-400 hover:bg-cyan-900/20 transition-colors cursor-default">
    {name}
  </span>
);

export default function Portfolio() {
  const [isScrolled, setIsScrolled] = useState(false);
  const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const navLinks = [
    { name: 'About', href: '#about' },
    { name: 'Experience', href: '#experience' },
    { name: 'Skills', href: '#skills' },
    { name: 'Projects', href: '#projects' },
    { name: 'Contact', href: '#contact' },
  ];

  return (
    <div className="min-h-screen bg-slate-900 text-slate-300 font-sans selection:bg-cyan-500/30">
      
      {/* Background Gradients */}
      <div className="fixed inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-0 left-0 w-96 h-96 bg-cyan-500/10 rounded-full blur-3xl -translate-x-1/2 -translate-y-1/2"></div>
        <div className="absolute bottom-0 right-0 w-96 h-96 bg-blue-600/10 rounded-full blur-3xl translate-x-1/2 translate-y-1/2"></div>
      </div>

      {/* Navigation */}
      <nav className={`fixed w-full z-50 transition-all duration-300 ${isScrolled ? 'bg-slate-900/90 backdrop-blur-md border-b border-slate-800 py-4' : 'bg-transparent py-6'}`}>
        <div className="container mx-auto px-6 flex justify-between items-center">
          <a href="#" className="text-2xl font-bold text-white tracking-tight">
            Sarwarish<span className="text-cyan-400">.dev</span>
          </a>

          {/* Desktop Nav */}
          <div className="hidden md:flex space-x-8">
            {navLinks.map((link) => (
              <a key={link.name} href={link.href} className="text-sm font-medium text-slate-400 hover:text-cyan-400 transition-colors">
                {link.name}
              </a>
            ))}
          </div>

          {/* Mobile Nav Toggle */}
          <button className="md:hidden text-white" onClick={() => setIsMobileMenuOpen(!isMobileMenuOpen)}>
            {isMobileMenuOpen ? <X size={24} /> : <Menu size={24} />}
          </button>
        </div>

        {/* Mobile Menu */}
        {isMobileMenuOpen && (
          <div className="md:hidden absolute top-full left-0 w-full bg-slate-800 border-b border-slate-700 py-4 px-6 flex flex-col space-y-4">
            {navLinks.map((link) => (
              <a 
                key={link.name} 
                href={link.href} 
                className="text-slate-300 hover:text-cyan-400"
                onClick={() => setIsMobileMenuOpen(false)}
              >
                {link.name}
              </a>
            ))}
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <section className="relative min-h-screen flex items-center pt-20">
        <div className="container mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
          <div className="space-y-6">
            <div className="inline-flex items-center space-x-2 px-3 py-1 rounded-full bg-cyan-900/30 border border-cyan-700/50 text-cyan-400 text-sm">
              <span className="w-2 h-2 rounded-full bg-cyan-400 animate-pulse"></span>
              <span>Open to Innovation</span>
            </div>
            
            <h1 className="text-5xl md:text-7xl font-bold text-white leading-tight">
              Building Robust <br />
              <span className="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-500">
                Scalable Systems
              </span>
            </h1>
            
            <p className="text-lg text-slate-400 max-w-lg">
              {PORTFOLIO_DATA.personal.summary}
            </p>

            <div className="flex flex-col sm:flex-row gap-4 pt-4">
              <a href="#contact" className="px-8 py-3 bg-cyan-500 text-slate-900 font-bold rounded-lg hover:bg-cyan-400 transition-all text-center">
                Contact Me
              </a>
              <a href={PORTFOLIO_DATA.personal.linkedin} target="_blank" rel="noreferrer" className="px-8 py-3 bg-slate-800 text-white font-bold rounded-lg border border-slate-700 hover:border-cyan-500 hover:text-cyan-400 transition-all flex items-center justify-center gap-2">
                <Linkedin size={20} />
                LinkedIn
              </a>
            </div>
          </div>

          <div className="relative hidden md:block">
             <div className="absolute inset-0 bg-gradient-to-r from-cyan-500 to-blue-600 rounded-2xl blur-2xl opacity-20 transform rotate-6"></div>
             <div className="relative bg-slate-800 border border-slate-700 rounded-2xl p-8 shadow-2xl">
                <div className="flex items-center space-x-2 mb-4 border-b border-slate-700 pb-4">
                  <div className="w-3 h-3 rounded-full bg-red-500"></div>
                  <div className="w-3 h-3 rounded-full bg-yellow-500"></div>
                  <div className="w-3 h-3 rounded-full bg-green-500"></div>
                  <span className="text-xs text-slate-500 ml-2">sarwarish_profile.cpp</span>
                </div>
                <pre className="font-mono text-sm text-slate-300 overflow-x-auto">
                  <code>
<span className="text-purple-400">class</span> <span className="text-yellow-400">Engineer</span> {'{'}
{'\n'}  <span className="text-purple-400">public:</span>
{'\n'}    <span className="text-blue-400">std::string</span> name = <span className="text-green-400">"{PORTFOLIO_DATA.personal.name}"</span>;
{'\n'}    <span className="text-blue-400">std::vector</span>&lt;<span className="text-blue-400">string</span>&gt; skills = {'{'}
{'\n'}      <span className="text-green-400">"Java"</span>, <span className="text-green-400">"C++"</span>, <span className="text-green-400">"Microservices"</span>
{'\n'}    {'}'};
{'\n'}
{'\n'}    <span className="text-purple-400">void</span> <span className="text-yellow-400">buildFuture</span>() {'{'}
{'\n'}      <span className="text-slate-500">// Deploying scalable solutions...</span>
{'\n'}      innovation.<span className="text-yellow-400">execute</span>();
{'\n'}    {'}'}
{'\n'} {'}'};
                  </code>
                </pre>
             </div>
          </div>
        </div>
      </section>

      {/* About / Stats Section */}
      <section id="about" className="py-20">
        <div className="container mx-auto px-6">
          <div className="grid grid-cols-2 md:grid-cols-4 gap-6">
            {[
              { label: "Experience", value: "3+", suffix: "Years" },
              { label: "Projects", value: "10+", suffix: "Completed" },
              { label: "Companies", value: "3", suffix: "MNCs" },
              { label: "Hackathons", value: "Top", suffix: "Finalist" }
            ].map((stat, idx) => (
              <div key={idx} className="bg-slate-800/30 p-6 rounded-xl border border-slate-700/50 text-center">
                <div className="text-3xl font-bold text-white mb-1">
                  {stat.value}
                  <span className="text-cyan-500">{stat.suffix}</span>
                </div>
                <div className="text-sm text-slate-400">{stat.label}</div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Experience Section */}
      <section id="experience" className="py-20 bg-slate-900/50">
        <div className="container mx-auto px-6">
          <SectionTitle title="Professional Journey" subtitle="My timeline of delivering value across leading tech companies." />
          
          <div className="max-w-4xl mx-auto space-y-8">
            {PORTFOLIO_DATA.experience.map((job, index) => (
              <div key={index} className="relative pl-8 md:pl-0">
                {/* Timeline Line (Desktop) */}
                <div className="hidden md:block absolute left-1/2 top-0 bottom-0 w-px bg-slate-800 -translate-x-1/2"></div>
                
                <div className={`md:flex items-center justify-between ${index % 2 === 0 ? 'md:flex-row-reverse' : ''} group`}>
                  {/* Dot */}
                  <div className="absolute left-0 md:left-1/2 w-4 h-4 bg-cyan-500 rounded-full border-4 border-slate-900 md:-translate-x-1/2 mt-6 md:mt-0 z-10"></div>
                  
                  {/* Content */}
                  <div className="md:w-5/12 mb-8 md:mb-0">
                    <Card className="h-full">
                      <div className="flex justify-between items-start mb-2">
                        <div>
                          <h3 className="text-xl font-bold text-white">{job.role}</h3>
                          <p className="text-cyan-400 text-sm font-medium">{job.company}</p>
                        </div>
                        <span className="text-xs text-slate-500 bg-slate-900 px-2 py-1 rounded border border-slate-700">{job.duration}</span>
                      </div>
                      <p className="text-slate-400 text-sm mb-4 leading-relaxed">
                        {job.description}
                      </p>
                      <div className="flex flex-wrap gap-2">
                        {job.tech.map(t => (
                          <span key={t} className="text-xs text-slate-300 bg-slate-700/50 px-2 py-0.5 rounded">
                            {t}
                          </span>
                        ))}
                      </div>
                    </Card>
                  </div>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Skills Section */}
      <section id="skills" className="py-20">
        <div className="container mx-auto px-6">
          <SectionTitle title="Technical Arsenal" subtitle="A comprehensive list of technologies I use to solve problems." />
          
          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Code className="text-cyan-400" size={24} />
                <h3 className="text-lg font-bold text-white">Languages</h3>
              </div>
              <div className="flex flex-wrap gap-2">
                {PORTFOLIO_DATA.skills.languages.map(skill => <SkillTag key={skill} name={skill} />)}
              </div>
            </Card>

            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Terminal className="text-purple-400" size={24} />
                <h3 className="text-lg font-bold text-white">Backend & Systems</h3>
              </div>
              <div className="flex flex-wrap gap-2">
                {PORTFOLIO_DATA.skills.backend.map(skill => <SkillTag key={skill} name={skill} />)}
              </div>
            </Card>

            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Cloud className="text-blue-400" size={24} />
                <h3 className="text-lg font-bold text-white">Cloud & DevOps</h3>
              </div>
              <div className="flex flex-wrap gap-2">
                {PORTFOLIO_DATA.skills.devops.map(skill => <SkillTag key={skill} name={skill} />)}
              </div>
            </Card>

            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Cpu className="text-green-400" size={24} />
                <h3 className="text-lg font-bold text-white">Frontend</h3>
              </div>
              <div className="flex flex-wrap gap-2">
                {PORTFOLIO_DATA.skills.frontend.map(skill => <SkillTag key={skill} name={skill} />)}
              </div>
            </Card>

            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Database className="text-orange-400" size={24} />
                <h3 className="text-lg font-bold text-white">Tools</h3>
              </div>
              <div className="flex flex-wrap gap-2">
                {PORTFOLIO_DATA.skills.tools.map(skill => <SkillTag key={skill} name={skill} />)}
              </div>
            </Card>

            <Card>
              <div className="flex items-center gap-3 mb-4">
                <Award className="text-yellow-400" size={24} />
                <h3 className="text-lg font-bold text-white">Certifications</h3>
              </div>
              <ul className="space-y-2">
                {PORTFOLIO_DATA.certifications.map((cert, i) => (
                  <li key={i} className="text-sm text-slate-400 flex items-start gap-2">
                    <span className="mt-1.5 w-1.5 h-1.5 rounded-full bg-cyan-500 shrink-0"></span>
                    {cert}
                  </li>
                ))}
              </ul>
            </Card>
          </div>
        </div>
      </section>

      {/* Internships / Projects Preview */}
      <section id="projects" className="py-20 bg-slate-800/30">
        <div className="container mx-auto px-6">
          <SectionTitle title="Notable Internships" subtitle="Early career achievements and project work." />
          
          <div className="grid md:grid-cols-2 gap-8 max-w-4xl mx-auto">
            {PORTFOLIO_DATA.internships.map((intern, i) => (
              <div key={i} className="group relative bg-slate-900 border border-slate-700 rounded-xl overflow-hidden hover:border-cyan-500/50 transition-all">
                <div className="p-8">
                  <div className="flex justify-between items-start mb-4">
                     <h3 className="text-xl font-bold text-white group-hover:text-cyan-400 transition-colors">{intern.role}</h3>
                     <ExternalLink size={18} className="text-slate-500 group-hover:text-cyan-400" />
                  </div>
                  <h4 className="text-sm text-slate-400 mb-4">{intern.company} • {intern.duration}</h4>
                  <p className="text-slate-300 text-sm leading-relaxed">
                    {intern.description}
                  </p>
                </div>
                <div className="h-1 w-full bg-gradient-to-r from-cyan-500 to-blue-600 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-20">
        <div className="container mx-auto px-6">
          <SectionTitle title="Get In Touch" subtitle="Currently exploring new opportunities. Feel free to reach out." />
          
          <div className="max-w-2xl mx-auto">
            <Card className="text-center py-12">
              <div className="inline-flex p-4 rounded-full bg-cyan-900/20 text-cyan-400 mb-6">
                <Mail size={32} />
              </div>
              <h3 className="text-2xl font-bold text-white mb-2">Let's start a conversation</h3>
              <p className="text-slate-400 mb-8 px-6">
                Whether you have a question about my experience, my tech stack, or just want to say hi, my inbox is always open.
              </p>
              
              <div className="flex flex-col sm:flex-row justify-center gap-4 px-6">
                <a 
                  href={`mailto:${PORTFOLIO_DATA.personal.email}`} 
                  className="px-8 py-3 bg-cyan-500 hover:bg-cyan-400 text-slate-900 font-bold rounded-lg transition-all"
                >
                  Send Email
                </a>
                <a 
                  href={PORTFOLIO_DATA.personal.linkedin} 
                  target="_blank" 
                  rel="noreferrer" 
                  className="px-8 py-3 bg-transparent border border-slate-600 hover:border-cyan-400 text-white font-bold rounded-lg transition-all"
                >
                  Connect on LinkedIn
                </a>
              </div>
            </Card>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="py-8 border-t border-slate-800 bg-slate-900 text-center">
        <p className="text-slate-500 text-sm">
          © {new Date().getFullYear()} Sarwarish Upadhyay. Built with React.js & Tailwind.
        </p>
      </footer>
    </div>
  );
}
