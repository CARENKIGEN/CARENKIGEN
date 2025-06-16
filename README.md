import { useState } from "react";
import { motion } from "framer-motion";
import { Github, Mail, Linkedin, Twitter, Code, Star, GitFork, Users, Copy, Download, Award } from "lucide-react";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Badge } from "@/components/ui/badge";
import { Input } from "@/components/ui/input";
import { Label } from "@/components/ui/label";
import { Textarea } from "@/components/ui/textarea";
import { toast } from "sonner";

const Index = () => {
  const [formData, setFormData] = useState({
    name: "Caren Chepkoech",
    username: "CARENKIGEN",
    title: "Full-Stack Developer",
    description: "Building amazing applications with modern technologies",
    email: "karenchepkoech2002@gmail.com",
    linkedin: "caren-chepkoech-474924266",
    twitter: "",
  });

  const languages = [
    { name: "JavaScript", percentage: 35, color: "#f1e05a" },
    { name: "TypeScript", percentage: 25, color: "#2b7489" },
    { name: "Python", percentage: 20, color: "#3572A5" },
    { name: "React", percentage: 15, color: "#61dafb" },
    { name: "CSS", percentage: 5, color: "#563d7c" },
  ];

  const stats = [
    { icon: Star, label: "Total Stars", value: "1.2k" },
    { icon: GitFork, label: "Total Forks", value: "340" },
    { icon: Code, label: "Total Commits", value: "2.1k" },
    { icon: Users, label: "Followers", value: "890" },
    { icon: Award, label: "Project Grade", value: "A+" },
  ];

  const generateReadme = () => {
    return `# Hi 👋, I'm ${formData.name || "Your Name"}

## ${formData.title}

${formData.description}

---

### 🚀 About Me
- 🔭 I'm currently working on **exciting projects**
- 🌱 I'm currently learning **new technologies**
- 💬 Ask me about **React, Node.js, Python**
- 📫 How to reach me: **${formData.email || "your.email@example.com"}**
- ⚡ Fun fact: **I love turning coffee into code!**

---

### 🛠️ Languages and Tools:

<p align="left">
<a href="https://reactjs.org/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a>
<a href="https://www.javascript.com/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a>
<a href="https://www.typescriptlang.org/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="typescript" width="40" height="40"/> </a>
<a href="https://nodejs.org" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a>
<a href="https://www.python.org" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
</p>

---

### 📊 GitHub Stats:

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=${formData.username || "YOUR_GITHUB_USERNAME"}&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F&icon_color=F85D7F&text_color=FFFFFF" alt="GitHub Stats" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=${formData.username || "YOUR_GITHUB_USERNAME"}&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F&text_color=FFFFFF" alt="Top Languages" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=${formData.username || "YOUR_GITHUB_USERNAME"}&theme=radical&hide_border=true&background=0D1117&stroke=F85D7F&ring=F85D7F&fire=F85D7F&currStreakLabel=FFFFFF" alt="GitHub Streak" />
</p>

---

### 🏆 Project Grade: A+ (Based on ${formData.username ? 'Quality & Quantity of Projects' : 'Project Analysis'})

<p align="center">
  <img src="https://img.shields.io/badge/Grade-A+-brightgreen?style=for-the-badge&logo=github&logoColor=white" alt="Project Grade" />
  <img src="https://img.shields.io/badge/Projects-High%20Quality-blue?style=for-the-badge&logo=star&logoColor=white" alt="Project Quality" />
</p>

---

### 🌟 GitHub Activity Graph:

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=${formData.username || "YOUR_GITHUB_USERNAME"}&bg_color=0D1117&color=F85D7F&line=F85D7F&point=FFFFFF&area=true&hide_border=true" alt="GitHub Activity Graph" />
</p>

---

### 🏆 GitHub Trophies:

<p align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=${formData.username || "YOUR_GITHUB_USERNAME"}&theme=radical&no-frame=true&no-bg=true&margin-w=4" alt="GitHub Trophies" />
</p>

---

### 🤝 Connect with me:

<p align="center">
${formData.linkedin ? `<a href="https://linkedin.com/in/${formData.linkedin}"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>` : ''}

${formData.email ? `<a href="mailto:${formData.email}"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>` : ''}
</p>

---

### 📈 Profile Views:

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=${formData.username || "YOUR_GITHUB_USERNAME"}&label=Profile%20views&color=0e75b6&style=flat" alt="Profile Views" />
</p>

---

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=100&section=footer" alt="Footer" />
</p>
`;
  };

  const copyToClipboard = async () => {
    const readme = generateReadme();
    try {
      await navigator.clipboard.writeText(readme);
      toast.success("README copied to clipboard!");
    } catch (err) {
      toast.error("Failed to copy README");
    }
  };

  const downloadReadme = () => {
    const readme = generateReadme();
    const blob = new Blob([readme], { type: 'text/markdown' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'README.md';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
    toast.success("README downloaded!");
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900">
      {/* Animated Background */}
      <div className="absolute inset-0 overflow-hidden">
        <div className="absolute -inset-10 opacity-50">
          <div className="absolute top-1/4 left-1/4 w-72 h-72 bg-purple-500 rounded-full mix-blend-multiply filter blur-xl animate-pulse"></div>
          <div className="absolute top-3/4 right-1/4 w-72 h-72 bg-blue-500 rounded-full mix-blend-multiply filter blur-xl animate-pulse animation-delay-2000"></div>
          <div className="absolute bottom-1/4 left-1/2 w-72 h-72 bg-pink-500 rounded-full mix-blend-multiply filter blur-xl animate-pulse animation-delay-4000"></div>
        </div>
      </div>

      <div className="relative z-10 container mx-auto px-4 py-16">
        {/* Header Section */}
        <motion.div
          initial={{ opacity: 0, y: -50 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.8 }}
          className="text-center mb-16"
        >
          <motion.h1
            className="text-6xl md:text-8xl font-bold bg-gradient-to-r from-blue-400 via-purple-500 to-pink-500 bg-clip-text text-transparent mb-6"
            animate={{ 
              backgroundPosition: ["0% 50%", "100% 50%", "0% 50%"],
            }}
            transition={{ 
              duration: 3, 
              repeat: Infinity, 
              ease: "linear" 
            }}
          >
            GitHub Profile
          </motion.h1>
          <motion.p
            initial={{ opacity: 0 }}
            animate={{ opacity: 1 }}
            transition={{ delay: 0.3, duration: 0.8 }}
            className="text-xl md:text-2xl text-gray-300 mb-8 max-w-3xl mx-auto"
          >
            Create a stunning GitHub README with live language statistics and beautiful animations
          </motion.p>
          
          <motion.div
            initial={{ opacity: 0, y: 30 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: 0.5, duration: 0.8 }}
            className="flex flex-wrap justify-center gap-4 mb-8"
          >
            {["📊 Live GitHub Stats", "🎨 Beautiful Design", "⚡ Easy to Use"].map((item, index) => (
              <Badge key={index} variant="secondary" className="text-sm px-4 py-2 bg-white/10 text-white border-white/20">
                {item}
              </Badge>
            ))}
          </motion.div>
        </motion.div>

        {/* Main Content */}
        <div className="grid lg:grid-cols-2 gap-8">
          {/* Generator Form */}
          <motion.div
            initial={{ opacity: 0, x: -50 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ delay: 0.7, duration: 0.8 }}
          >
            <Card className="bg-white/10 backdrop-blur-lg border-white/20">
              <CardHeader>
                <CardTitle className="text-white text-2xl">README Generator</CardTitle>
              </CardHeader>
              <CardContent className="space-y-6">
                <div className="grid md:grid-cols-2 gap-4">
                  <div>
                    <Label htmlFor="name" className="text-white">Your Name</Label>
                    <Input
                      id="name"
                      value={formData.name}
                      onChange={(e) => setFormData({...formData, name: e.target.value})}
                      placeholder="John Doe"
                      className="bg-white/10 border-white/20 text-white"
                    />
                  </div>
                  <div>
                    <Label htmlFor="username" className="text-white">GitHub Username</Label>
                    <Input
                      id="username"
                      value={formData.username}
                      onChange={(e) => setFormData({...formData, username: e.target.value})}
                      placeholder="johndoe"
                      className="bg-white/10 border-white/20 text-white"
                    />
                  </div>
                </div>
                
                <div>
                  <Label htmlFor="title" className="text-white">Professional Title</Label>
                  <Input
                    id="title"
                    value={formData.title}
                    onChange={(e) => setFormData({...formData, title: e.target.value})}
                    placeholder="Full-Stack Developer"
                    className="bg-white/10 border-white/20 text-white"
                  />
                </div>
                
                <div>
                  <Label htmlFor="description" className="text-white">Description</Label>
                  <Textarea
                    id="description"
                    value={formData.description}
                    onChange={(e) => setFormData({...formData, description: e.target.value})}
                    placeholder="Brief description about yourself"
                    className="bg-white/10 border-white/20 text-white"
                  />
                </div>
                
                <div className="grid md:grid-cols-3 gap-4">
                  <div>
                    <Label htmlFor="email" className="text-white">Email</Label>
                    <Input
                      id="email"
                      type="email"
                      value={formData.email}
                      onChange={(e) => setFormData({...formData, email: e.target.value})}
                      placeholder="john@example.com"
                      className="bg-white/10 border-white/20 text-white"
                    />
                  </div>
                  <div>
                    <Label htmlFor="linkedin" className="text-white">LinkedIn Username</Label>
                    <Input
                      id="linkedin"
                      value={formData.linkedin}
                      onChange={(e) => setFormData({...formData, linkedin: e.target.value})}
                      placeholder="johndoe"
                      className="bg-white/10 border-white/20 text-white"
                    />
                  </div>
                  <div>
                    <Label htmlFor="twitter" className="text-white">Twitter Username</Label>
                    <Input
                      id="twitter"
                      value={formData.twitter}
                      onChange={(e) => setFormData({...formData, twitter: e.target.value})}
                      placeholder="johndoe"
                      className="bg-white/10 border-white/20 text-white"
                    />
                  </div>
                </div>
                
                <div className="flex gap-4 pt-4">
                  <Button
                    onClick={copyToClipboard}
                    className="flex-1 bg-gradient-to-r from-blue-500 to-purple-600 hover:from-blue-600 hover:to-purple-700"
                  >
                    <Copy className="w-4 h-4 mr-2" />
                    Copy README
                  </Button>
                  <Button
                    onClick={downloadReadme}
                    variant="outline"
                    className="flex-1 border-white/20 text-white hover:bg-white/20"
                  >
                    <Download className="w-4 h-4 mr-2" />
                    Download README
                  </Button>
                </div>
              </CardContent>
            </Card>
          </motion.div>

          {/* Preview Section */}
          <motion.div
            initial={{ opacity: 0, x: 50 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ delay: 0.7, duration: 0.8 }}
            className="space-y-8"
          >
            {/* Stats Section */}
            <div className="grid grid-cols-2 gap-4">
              {stats.map((stat, index) => (
                <Card key={index} className="bg-white/10 backdrop-blur-lg border-white/20 hover:bg-white/20 transition-all duration-300">
                  <CardContent className="p-4 text-center">
                    <stat.icon className="w-6 h-6 mx-auto mb-2 text-blue-400" />
                    <div className="text-lg font-bold text-white mb-1">{stat.value}</div>
                    <div className="text-xs text-gray-300">{stat.label}</div>
                  </CardContent>
                </Card>
              ))}
            </div>

            {/* Language Statistics */}
            <Card className="bg-white/10 backdrop-blur-lg border-white/20">
              <CardHeader>
                <CardTitle className="text-white text-lg">🚀 Languages & Technologies</CardTitle>
              </CardHeader>
              <CardContent className="space-y-4">
                {languages.map((lang, index) => (
                  <motion.div
                    key={lang.name}
                    initial={{ opacity: 0, x: -30 }}
                    animate={{ opacity: 1, x: 0 }}
                    transition={{ delay: index * 0.1, duration: 0.5 }}
                    className="space-y-2"
                  >
                    <div className="flex justify-between items-center">
                      <span className="text-white font-medium text-sm">{lang.name}</span>
                      <span className="text-gray-300 text-sm">{lang.percentage}%</span>
                    </div>
                    <div className="w-full bg-gray-700 rounded-full h-2">
                      <motion.div
                        className="h-2 rounded-full"
                        style={{ backgroundColor: lang.color }}
                        initial={{ width: 0 }}
                        animate={{ width: `${lang.percentage}%` }}
                        transition={{ delay: index * 0.1, duration: 1, ease: "easeOut" }}
                      />
                    </div>
                  </motion.div>
                ))}
              </CardContent>
            </Card>

            {/* GitHub Stats Images */}
            <div className="space-y-4">
              <h3 className="text-xl font-bold text-white text-center">📊 GitHub Statistics</h3>
              <div className="space-y-4">
                <Card className="bg-white/10 backdrop-blur-lg border-white/20 overflow-hidden">
                  <CardContent className="p-2">
                    <img
                      src={`https://github-readme-stats.vercel.app/api?username=${formData.username || "YOUR_GITHUB_USERNAME"}&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F&icon_color=F85D7F&text_color=FFFFFF`}
                      alt="GitHub Stats"
                      className="w-full h-auto rounded"
                    />
                  </CardContent>
                </Card>
                <Card className="bg-white/10 backdrop-blur-lg border-white/20 overflow-hidden">
                  <CardContent className="p-2">
                    <img
                      src={`https://github-readme-stats.vercel.app/api/top-langs/?username=${formData.username || "YOUR_GITHUB_USERNAME"}&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=F85D7F&text_color=FFFFFF`}
                      alt="Top Languages"
                      className="w-full h-auto rounded"
                    />
                  </CardContent>
                </Card>
              </div>
            </div>

            {/* Contact Section with clickable links */}
            <div className="text-center">
              <h3 className="text-xl font-bold text-white mb-4">🤝 Let's Connect</h3>
              <div className="flex flex-wrap justify-center gap-2">
                <Button
                  variant="outline"
                  size="sm"
                  className="bg-white/10 border-white/20 text-white hover:bg-white/20 transition-all duration-300 group"
                  onClick={() => window.open(`https://github.com/${formData.username}`, '_blank')}
                >
                  <Github className="w-4 h-4 mr-1 group-hover:rotate-12 transition-transform" />
                  GitHub
                </Button>
                {formData.linkedin && (
                  <Button
                    variant="outline"
                    size="sm"
                    className="bg-white/10 border-white/20 text-white hover:bg-white/20 transition-all duration-300 group"
                    onClick={() => window.open(`https://linkedin.com/in/${formData.linkedin}`, '_blank')}
                  >
                    <Linkedin className="w-4 h-4 mr-1 group-hover:rotate-12 transition-transform" />
                    LinkedIn
                  </Button>
                )}
                {formData.twitter && (
                  <Button
                    variant="outline"
                    size="sm"
                    className="bg-white/10 border-white/20 text-white hover:bg-white/20 transition-all duration-300 group"
                    onClick={() => window.open(`https://twitter.com/${formData.twitter}`, '_blank')}
                  >
                    <Twitter className="w-4 h-4 mr-1 group-hover:rotate-12 transition-transform" />
                    Twitter
                  </Button>
                )}
                {formData.email && (
                  <Button
                    variant="outline"
                    size="sm"
                    className="bg-white/10 border-white/20 text-white hover:bg-white/20 transition-all duration-300 group"
                    onClick={() => window.open(`mailto:${formData.email}`, '_blank')}
                  >
                    <Mail className="w-4 h-4 mr-1 group-hover:rotate-12 transition-transform" />
                    Email
                  </Button>
                )}
              </div>
            </div>
          </motion.div>
        </div>
      </div>
    </div>
  );
};

export default Index;
