import { useState } from "react";
import { motion } from "framer-motion";
import {
  LineChart,
  Line,
  BarChart,
  Bar,
  XAxis,
  YAxis,
  Tooltip as ReTooltip,
  ResponsiveContainer,
} from "recharts";
import {
  CheckCircle2,
  Circle,
  Moon,
  Sun,
  MessageSquare,
  BookOpen,
  LineChart as LineChartIcon,
  BarChart3,
} from "lucide-react";
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Switch } from "@/components/ui/switch";
import { Progress } from "@/components/ui/progress";
import {
  Tabs,
  TabsContent,
  TabsList,
  TabsTrigger,
} from "@/components/ui/tabs";
import {
  Tooltip,
  TooltipContent,
  TooltipProvider,
  TooltipTrigger,
} from "@/components/ui/tooltip";
import { Badge } from "@/components/ui/badge";

// Fake data for charts
const lineData = [
  { name: "Mon", value: 30 },
  { name: "Tue", value: 50 },
  { name: "Wed", value: 40 },
  { name: "Thu", value: 70 },
  { name: "Fri", value: 60 },
];

const barData = [
  { name: "Feature A", users: 400 },
  { name: "Feature B", users: 300 },
  { name: "Feature C", users: 200 },
  { name: "Feature D", users: 278 },
];

const defaultChecklist = [
  { id: 1, label: "Complete profile setup", done: true },
  { id: 2, label: "Connect integrations", done: false },
  { id: 3, label: "Invite team members", done: false },
  { id: 4, label: "Create first project", done: false },
];

type ChecklistItem = typeof defaultChecklist[number];

export default function Dashboard() {
  const [dark, setDark] = useState(false);
  const [items, setItems] = useState<ChecklistItem[]>(defaultChecklist);
  const [messages, setMessages] = useState([
    { from: "ai", text: "Welcome! Need help getting started?" },
  ]);
  const [input, setInput] = useState("");

  const sendMessage = () => {
    if (!input.trim()) return;
    setMessages([...messages, { from: "user", text: input }]);
    setInput("");
    // Fake AI reply
    setTimeout(
      () =>
        setMessages((m) => [
          ...m,
          { from: "ai", text: "This is a placeholder AI response." },
        ]),
      600
    );
  };

  return (
    <div className={dark ? "dark" : ""}>
      <div className="min-h-screen bg-gray-50 dark:bg-neutral-900 text-gray-900 dark:text-gray-100 transition-colors">
        {/* Header */}
        <header className="flex items-center justify-between p-4 border-b dark:border-neutral-800">
          <h1 className="text-xl font-bold">AI-Powered Interactive Onboarding</h1>
          <div className="flex items-center gap-3">
            <TooltipProvider>
              <Tooltip>
                <TooltipTrigger asChild>
                  <Button variant="outline" size="icon" onClick={() => setDark(!dark)}>
                    {dark ? <Sun className="h-5 w-5" /> : <Moon className="h-5 w-5" />}
                  </Button>
                </TooltipTrigger>
                <TooltipContent>Toggle theme</TooltipContent>
              </Tooltip>
            </TooltipProvider>
          </div>
        </header>

        {/* Content */}
        <main className="grid grid-cols-1 lg:grid-cols-3 gap-4 p-4">
          <div className="lg:col-span-2 space-y-4">
            <Tabs defaultValue="checklist">
              <TabsList>
                <TabsTrigger value="checklist">Checklist</TabsTrigger>
                <TabsTrigger value="metrics">Metrics</TabsTrigger>
                <TabsTrigger value="activity">Activity</TabsTrigger>
              </TabsList>
              <TabsContent value="checklist">
                <Checklist items={items} setItems={setItems} />
              </TabsContent>
              <TabsContent value="metrics">
                <Metrics />
              </TabsContent>
              <TabsContent value="activity">
                <Activity />
              </TabsContent>
            </Tabs>
          </div>

          <div className="space-y-4">
            <AIChat messages={messages} input={input} setInput={setInput} sendMessage={sendMessage} />
            <Resources />
          </div>
        </main>
      </div>
    </div>
  );
}

// Checklist Component
function Checklist({ items, setItems }: { items: ChecklistItem[]; setItems: (items: ChecklistItem[]) => void }) {
  const completed = items.filter((i) => i.done).length;
  const pct = Math.round((completed / items.length) * 100);

  return (
    <Card className="h-full">
      <CardHeader>
        <CardTitle className="flex items-center gap-2">
          <CheckCircle2 className="h-5 w-5" />
          Your checklist <Badge variant="outline">{pct}%</Badge>
        </CardTitle>
      </CardHeader>
      <CardContent className="space-y-3">
        {items.map((item) => (
          <button
            key={item.id}
            onClick={() => setItems(items.map((x) => x.id === item.id ? { ...x, done: !x.done } : x))}
            className="w-full flex items-center gap-3 rounded-2xl border p-3 text-left hover:bg-muted/50 dark:border-neutral-800"
          >
            {item.done ? <CheckCircle2 className="h-5 w-5" /> : <Circle className="h-5 w-5" />}
            <span className={item.done ? "line-through text-muted-foreground" : ""}>{item.label}</span>
          </button>
        ))}
      </CardContent>
      <Progress value={pct} className="mt-2" />
    </Card>
  );
}

// Metrics Component
function Metrics() {
  return (
    <div className="grid md:grid-cols-2 gap-4">
      <Card>
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><LineChartIcon className="h-5 w-5" />Weekly Engagement</CardTitle>
        </CardHeader>
        <CardContent>
          <ResponsiveContainer width="100%" height={200}>
            <LineChart data={lineData}>
              <XAxis dataKey="name" />
              <YAxis />
              <ReTooltip />
              <Line type="monotone" dataKey="value" stroke="currentColor" strokeWidth={2} />
            </LineChart>
          </ResponsiveContainer>
        </CardContent>
      </Card>
      <Card>
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><BarChart3 className="h-5 w-5" />Feature Adoption</CardTitle>
        </CardHeader>
        <CardContent>
          <ResponsiveContainer width="100%" height={200}>
            <BarChart data={barData}>
              <XAxis dataKey="name" />
              <YAxis />
              <ReTooltip />
              <Bar dataKey="users" fill="currentColor" />
            </BarChart>
          </ResponsiveContainer>
        </CardContent>
      </Card>
    </div>
  );
}

// Activity Component
function Activity() {
  const activities = [
    "User John created a project",
    "Integration with Slack enabled",
    "Maria invited 3 new team members",
    "First milestone achieved!",
  ];

  return (
    <Card>
      <CardHeader>
        <CardTitle>Recent Activity</CardTitle>
      </CardHeader>
      <CardContent>
        <ul className="space-y-2">
          {activities.map((a, i) => (
            <motion.li
              key={i}
              initial={{ opacity: 0, x: -10 }}
              animate={{ opacity: 1, x: 0 }}
              transition={{ delay: i * 0.1 }}
              className="p-2 rounded-lg bg-muted/30"
            >
              {a}
            </motion.li>
          ))}
        </ul>
      </CardContent>
    </Card>
  );
}

// AI Chat Component
function AIChat({ messages, input, setInput, sendMessage }: { messages: { from: string; text: string }[]; input: string; setInput: (x: string) => void; sendMessage: () => void }) {
  return (
    <Card className="h-[400px] flex flex-col">
      <CardHeader>
        <CardTitle className="flex items-center gap-2"><MessageSquare className="h-5 w-5" />AI Assistant</CardTitle>
      </CardHeader>
      <CardContent className="flex-1 overflow-y-auto space-y-2">
        {messages.map((m, i) => (
          <div key={i} className={`p-2 rounded-xl ${m.from === "ai" ? "bg-blue-500/10 text-blue-900 dark:text-blue-100" : "bg-green-500/10 text-green-900 dark:text-green-100"}`}>
            {m.text}
          </div>
        ))}
      </CardContent>
      <div className="p-2 flex gap-2 border-t dark:border-neutral-800">
        <Input value={input} onChange={(e) => setInput(e.target.value)} onKeyDown={(e) => e.key === "Enter" && sendMessage()} placeholder="Ask me anything..." />
        <Button onClick={sendMessage}>Send</Button>
      </div>
    </Card>
  );
}

// Resources Component
function Resources() {
  return (
    <Card>
      <CardHeader>
        <CardTitle className="flex items-center gap-2"><BookOpen className="h-5 w-5" />Resources</CardTitle>
      </CardHeader>
      <CardContent className="space-y-2">
        <a href="#" className="block p-2 rounded-lg bg-muted/30 hover:bg-muted">📘 Getting Started Guide</a>
        <a href="#" className="block p-2 rounded-lg bg-muted/30 hover:bg-muted">📹 Product Tour Video</a>
        <a href="#" className="block p-2 rounded-lg bg-muted/30 hover:bg-muted">💬 Join Community Forum</a>
      </CardContent>
    </Card>
  );
}
