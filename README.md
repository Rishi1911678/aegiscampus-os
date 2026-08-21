# aegiscampus-os
import React, { useState } from "react";
import {
  ShieldAlert,
  Search,
  GraduationCap,
  Briefcase,
  Calendar,
  Clock,
  MapPin,
  X,
  Folder,
  FolderOpen,
  CreditCard,
  Building,
  UserCheck,
  ChevronRight,
  QrCode,
  CheckCircle2,
  PlusCircle,
  Sparkles,
  Filter,
  Ambulance,
  Radio,
  Check
} from "lucide-react";

export default function App() {
  const [activeTab, setActiveTab] = useState("safety");
  const [selectedMapIncident, setSelectedMapIncident] = useState(null);
  const [searchTerm, setSearchTerm] = useState("");
  const [selectedDeptFilter, setSelectedDeptFilter] = useState("ALL");

  // STUDENT DATASET WITH DEPARTMENT TAGS
  const [studentFolderDb] = useState([
    {
      id: "23BCE1042",
      name: "Aarav Sharma",
      deptCode: "CSE",
      dept: "Computer Science & Engineering",
      avatar: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150&auto=format&fit=crop&q=80",
      overview: { gpa: "9.2", cpa: "9.1", att: "96%", credits: 112, status: "Active" },
      folders: {
        academics: {
          cgpaHistory: [
            { sem: "Sem 1", gpa: "9.0" },
            { sem: "Sem 2", gpa: "9.1" },
            { sem: "Sem 3", gpa: "9.4" },
            { sem: "Sem 4", gpa: "9.3" }
          ],
          major: "Software Engineering",
          minor: "Cybersecurity"
        },
        faculty: [
          { role: "Faculty Advisor", name: "Dr. S. Ramanathan", cabin: "AB1-302", email: "ramanathan.s@vit.ac.in" },
          { role: "Class Teacher", name: "Dr. Meera Vasudevan", cabin: "AB2-402", email: "meera.v@vit.ac.in" }
        ],
        fees: {
          tuitionFee: "₹ 1,98,000",
          hostelFee: "₹ 85,000",
          status: "Paid & Cleared",
          receiptNo: "REC-2026-90421",
          dueDate: "2026-07-15",
          hallTicketEligible: true
        },
        placement: {
          eligibility: "Eligible for Tier-1",
          registeredDrives: 14,
          shortlists: 3,
          offers: [{ company: "TechCorp Labs", package: "24 LPA", role: "SDE-1" }],
          resumeStatus: "Verified"
        },
        hostel: {
          type: "Hosteller",
          block: "Block D1",
          room: "302-A (AC 2-Bed)",
          warden: "Mr. V. Suresh",
          messType: "Special South Indian Mess"
        },
        timetable: [
          { time: "08:00 - 08:50 AM", mon: "CSE3001 (AB-1 302)", tue: "MAT2001 (AB-2 101)", wed: "ECE2004 (AB-1 204)" },
          { time: "09:00 - 09:50 AM", mon: "MAT2001 (AB-2 101)", tue: "CSE3001 (AB-1 302)", wed: "CSE3002 (Lab 4)" }
        ],
        exams: [
          { code: "CSE3001", subject: "Software Engineering", date: "2026-09-12", slot: "10:00 AM", hall: "AB-1 302", seat: "C-12" }
        ]
      }
    },
    {
      id: "24ECE0118",
      name: "Ananya Subramanian",
      deptCode: "ECE",
      dept: "Electronics & Comm. Engg",
      avatar: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150&auto=format&fit=crop&q=80",
      overview: { gpa: "8.8", cpa: "8.7", att: "92%", credits: 78, status: "Active" },
      folders: {
        academics: {
          cgpaHistory: [
            { sem: "Sem 1", gpa: "8.6" },
            { sem: "Sem 2", gpa: "8.8" },
            { sem: "Sem 3", gpa: "8.9" }
          ],
          major: "VLSI Design",
          minor: "Robotics"
        },
        faculty: [
          { role: "Faculty Advisor", name: "Dr. Meera Vasudevan", cabin: "AB2-402", email: "meera.v@vit.ac.in" }
        ],
        fees: {
          tuitionFee: "₹ 1,85,000",
          hostelFee: "₹ 0 (Day Scholar)",
          status: "Paid & Cleared",
          receiptNo: "REC-2026-88120",
          dueDate: "2026-07-15",
          hallTicketEligible: true
        },
        placement: {
          eligibility: "Eligible for Core & IT",
          registeredDrives: 8,
          shortlists: 1,
          offers: [],
          resumeStatus: "Verified"
        },
        hostel: {
          type: "Day Scholar",
          block: "N/A",
          room: "N/A",
          transportRoute: "Bus Route 04 - Adyar Express",
          pickupPoint: "Adyar Depot (06:45 AM)"
        },
        timetable: [
          { time: "08:00 - 08:50 AM", mon: "ECE2004 (AB-2 104)", tue: "ECE2001 (AB-2 201)", wed: "MAT2001 (AB-1 102)" }
        ],
        exams: [
          { code: "ECE2004", subject: "Digital Signal Processing", date: "2026-09-14", slot: "02:00 PM", hall: "AB-2 104", seat: "B-18" }
        ]
      }
    },
    {
      id: "23EEE0045",
      name: "Rohan Verma",
      deptCode: "EEE",
      dept: "Electrical & Electronics Engg",
      avatar: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150&auto=format&fit=crop&q=80",
      overview: { gpa: "8.9", cpa: "8.8", att: "94%", credits: 104, status: "Active" },
      folders: {
        academics: {
          cgpaHistory: [
            { sem: "Sem 1", gpa: "8.7" },
            { sem: "Sem 2", gpa: "8.9" },
            { sem: "Sem 3", gpa: "9.1" }
          ],
          major: "Power Systems & EV Technology",
          minor: "Embedded Systems"
        },
        faculty: [
          { role: "Faculty Advisor", name: "Dr. K. Nithya", cabin: "AB3-201", email: "nithya.k@vit.ac.in" }
        ],
        fees: {
          tuitionFee: "₹ 1,90,000",
          hostelFee: "₹ 82,000",
          status: "Paid & Cleared",
          receiptNo: "REC-2026-77301",
          dueDate: "2026-07-15",
          hallTicketEligible: true
        },
        placement: {
          eligibility: "Eligible for Core Electrical & IT",
          registeredDrives: 10,
          shortlists: 2,
          offers: [{ company: "ABB Energy Systems", package: "14 LPA", role: "Graduate Engineer Trainee" }],
          resumeStatus: "Verified"
        },
        hostel: {
          type: "Hosteller",
          block: "Block C2",
          room: "112-B (Non-AC 2-Bed)",
          warden: "Mr. R. Rajesh",
          messType: "North Indian Special Mess"
        },
        timetable: [
          { time: "09:00 - 09:50 AM", mon: "EEE3002 (AB-3 101)", tue: "EEE3004 (Lab 1)", wed: "MAT2001 (AB-1 202)" }
        ],
        exams: [
          { code: "EEE3002", subject: "Power Electronics Control", date: "2026-09-15", slot: "10:00 AM", hall: "AB-3 101", seat: "D-05" }
        ]
      }
    },
    {
      id: "22MECH0089",
      name: "Kavya Reddy",
      deptCode: "MECH",
      dept: "Mechanical Engineering",
      avatar: "https://images.unsplash.com/photo-1517841905240-472988babdf9?w=150&auto=format&fit=crop&q=80",
      overview: { gpa: "8.6", cpa: "8.5", att: "90%", credits: 130, status: "Active" },
      folders: {
        academics: {
          cgpaHistory: [
            { sem: "Sem 1", gpa: "8.4" },
            { sem: "Sem 2", gpa: "8.5" },
            { sem: "Sem 3", gpa: "8.7" }
          ],
          major: "Robotics & Automation",
          minor: "CAD/CAM Systems"
        },
        faculty: [
          { role: "Faculty Advisor", name: "Dr. P. Sundaram", cabin: "AB1-102", email: "sundaram.p@vit.ac.in" }
        ],
        fees: {
          tuitionFee: "₹ 1,80,000",
          hostelFee: "₹ 80,000",
          status: "Paid & Cleared",
          receiptNo: "REC-2026-66219",
          dueDate: "2026-07-15",
          hallTicketEligible: true
        },
        placement: {
          eligibility: "Eligible for Core Mechanical",
          registeredDrives: 12,
          shortlists: 4,
          offers: [{ company: "Bosch Mobility", package: "16 LPA", role: "Robotics Design Engineer" }],
          resumeStatus: "Verified"
        },
        hostel: {
          type: "Hosteller",
          block: "Block A1",
          room: "405-A (AC Single)",
          warden: "Mrs. L. Kamala",
          messType: "Special Multi-Cuisine Mess"
        },
        timetable: [
          { time: "10:00 - 10:50 AM", mon: "MECH4001 (AB-1 102)", tue: "MECH4005 (Robotics Lab)", wed: "MAT2001 (AB-2 201)" }
        ],
        exams: [
          { code: "MECH4001", subject: "Automated Kinematics & CAD", date: "2026-09-18", slot: "02:00 PM", hall: "AB-1 102", seat: "E-21" }
        ]
      }
    }
  ]);

  const [activeStudentId, setActiveStudentId] = useState("23BCE1042");
  const [activeFolderKey, setActiveFolderKey] = useState("academics");

  // QR PASS GENERATOR STATE
  const [passList, setPassList] = useState([
    {
      passId: "PASS-2026-8841",
      studentId: "23BCE1042",
      studentName: "Aarav Sharma",
      type: "Weekend Outing Pass",
      outTime: "2026-08-22 08:00 AM",
      inTime: "2026-08-22 08:30 PM",
      reason: "Medical Checkup & Personal Work",
      destination: "T. Nagar, Chennai",
      status: "APPROVED",
      approvedBy: "Hostel Warden (Mr. V. Suresh)",
      qrToken: "VIT-QR-AARAV-2026-X89"
    }
  ]);

  const [newPassType, setNewPassType] = useState("Weekend Outing Pass");
  const [newPassReason, setNewPassReason] = useState("");
  const [newPassDestination, setNewPassDestination] = useState("");
  const [newPassOutTime, setNewPassOutTime] = useState("2026-08-23 09:00 AM");
  const [newPassInTime, setNewPassInTime] = useState("2026-08-23 08:00 PM");

  const handleGeneratePass = (e) => {
    e.preventDefault();
    if (!newPassReason || !newPassDestination) return;

    const student = studentFolderDb.find((s) => s.id === activeStudentId) || studentFolderDb[0];
    const generatedId = `PASS-2026-${Math.floor(1000 + Math.random() * 9000)}`;
    const newPassObj = {
      passId: generatedId,
      studentId: student.id,
      studentName: student.name,
      type: newPassType,
      outTime: newPassOutTime,
      inTime: newPassInTime,
      reason: newPassReason,
      destination: newPassDestination,
      status: "APPROVED",
      approvedBy: "Auto-Approved ERP System",
      qrToken: `VIT-QR-${student.name.split(" ")[0].toUpperCase()}-${Math.floor(100 + Math.random() * 900)}`
    };

    setPassList([newPassObj, ...passList]);
    setNewPassReason("");
    setNewPassDestination("");
  };

  // ACCURATE RADAR INCIDENTS & DISPATCH STATUS
  const [incidents, setIncidents] = useState([
    {
      id: 201,
      type: "WOMEN'S SAFETY DISTRESS",
      locName: "Academic Block 1 (AB-1)",
      coords: { x: 380, y: 155 },
      time: "Just Now",
      statusStage: 1, // 0: Pending, 1: En Route, 2: Arrived
      statusText: "Patrol Patrol Unit 04 En Route",
      eta: "1.5 mins",
      responder: "Officer S. Kumar (Patrol-04)"
    },
    {
      id: 202,
      type: "CRITICAL MEDICAL ASSISTANCE",
      locName: "Medical Center Zone",
      coords: { x: 670, y: 360 },
      time: "2 mins ago",
      statusStage: 2,
      statusText: "First Aid Team On Scene",
      eta: "Arrived",
      responder: "Medical First Response Squad A"
    }
  ]);

  const handleDispatch = (id) => {
    setIncidents(
      incidents.map((inc) =>
        inc.id === id
          ? {
              ...inc,
              statusStage: 1,
              statusText: "Security Patrol Dispatched",
              eta: "2 mins"
            }
          : inc
      )
    );
    setSelectedMapIncident(null);
  };

  // FILTERED STUDENTS
  const filteredStudents = studentFolderDb.filter((s) => {
    const matchesDept = selectedDeptFilter === "ALL" || s.deptCode === selectedDeptFilter;
    const matchesSearch =
      s.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
      s.id.toLowerCase().includes(searchTerm.toLowerCase()) ||
      s.dept.toLowerCase().includes(searchTerm.toLowerCase());
    return matchesDept && matchesSearch;
  });

  const currentStudent =
    filteredStudents.find((s) => s.id === activeStudentId) || filteredStudents[0] || studentFolderDb[0];

  const handleDeptFilterChange = (code) => {
    setSelectedDeptFilter(code);
    const matched = studentFolderDb.filter((s) => code === "ALL" || s.deptCode === code);
    if (matched.length > 0) {
      setActiveStudentId(matched[0].id);
    }
  };

  return (
    <div className="min-h-screen bg-slate-950 text-slate-100 font-sans flex flex-col selection:bg-indigo-500 selection:text-white relative">
      {/* Header */}
      <header className="sticky top-0 z-40 bg-slate-900/90 backdrop-blur-xl border-b border-slate-800 px-6 py-3 flex flex-wrap items-center justify-between gap-4 shadow-2xl">
        <div className="flex items-center gap-3">
          <div className="bg-indigo-600/20 p-2 rounded-xl border border-indigo-500/40 shadow-[0_0_15px_rgba(79,70,229,0.3)]">
            <ShieldAlert className="h-6 w-6 text-indigo-400" />
          </div>
          <div>
            <h1 className="font-bold text-base tracking-wide bg-gradient-to-r from-indigo-400 via-cyan-400 to-indigo-200 bg-clip-text text-transparent">
              AegisCampus OS <span className="text-xs font-normal text-slate-400">| Department Directory</span>
            </h1>
            <p className="text-[10px] text-slate-400 tracking-wider">VIT Chennai Multi-Department ERP</p>
          </div>
        </div>

        {/* Navigation Tabs */}
        <nav className="flex items-center bg-slate-950/80 backdrop-blur-md p-1.5 rounded-xl border border-slate-800 gap-1 shadow-inner">
          <button
            onClick={() => setActiveTab("erp")}
            className={`flex items-center gap-1.5 px-3 py-1.5 rounded-lg text-xs font-semibold transition-all ${
              activeTab === "erp" ? "bg-indigo-600 text-white shadow-md" : "text-slate-400 hover:text-slate-200"
            }`}
          >
            <GraduationCap className="h-3.5 w-3.5" /> Student Folders ERP
          </button>

          <button
            onClick={() => setActiveTab("qrpass")}
            className={`flex items-center gap-1.5 px-3 py-1.5 rounded-lg text-xs font-semibold transition-all ${
              activeTab === "qrpass" ? "bg-indigo-600 text-white shadow-md" : "text-slate-400 hover:text-slate-200"
            }`}
          >
            <QrCode className="h-3.5 w-3.5 text-cyan-400" /> QR Pass Maker
          </button>

          <button
            onClick={() => setActiveTab("safety")}
            className={`flex items-center gap-1.5 px-3 py-1.5 rounded-lg text-xs font-semibold transition-all ${
              activeTab === "safety" ? "bg-indigo-600 text-white shadow-md" : "text-slate-400 hover:text-slate-200"
            }`}
          >
            <ShieldAlert className="h-3.5 w-3.5" /> Emergency Radar
          </button>
        </nav>
      </header>

      {/* Radar Incident Dispatch Modal */}
      {selectedMapIncident && (
        <div className="fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-950/80 backdrop-blur-md">
          <div className="bg-slate-900 border border-slate-700 rounded-2xl max-w-md w-full p-6 shadow-2xl space-y-5 relative">
            <div className="flex items-center justify-between border-b border-slate-800 pb-3">
              <div className="flex items-center gap-2">
                <MapPin className="h-5 w-5 text-indigo-400" />
                <h3 className="font-bold text-sm text-slate-100">Action Required: {selectedMapIncident.locName}</h3>
              </div>
              <button onClick={() => setSelectedMapIncident(null)} className="text-slate-400 hover:text-white">
                <X className="h-5 w-5" />
              </button>
            </div>
            <div className="bg-slate-950 p-4 rounded-xl border border-slate-800 space-y-2">
              <p className="text-xs text-slate-400">
                Incident Category: <strong className="text-slate-200 uppercase">{selectedMapIncident.type}</strong>
              </p>
              <p className="text-xs text-slate-400">
                Reported: <strong className="text-amber-400">{selectedMapIncident.time}</strong>
              </p>
              <p className="text-xs text-slate-400">
                Current Emergency Status: <strong className="text-cyan-400">{selectedMapIncident.statusText}</strong>
              </p>
            </div>
            <button
              onClick={() => handleDispatch(selectedMapIncident.id)}
              className="w-full py-3 px-4 rounded-xl bg-red-600 hover:bg-red-500 text-white font-bold text-xs shadow-lg transition"
            >
              DISPATCH / UPDATE SECURITY PATROL
            </button>
          </div>
        </div>
      )}

      <main className="flex-1 p-6 max-w-7xl mx-auto w-full">
        {/* TAB 1: STUDENT FOLDERS ERP */}
        {activeTab === "erp" && (
          <div className="space-y-6">
            <div className="flex flex-col md:flex-row items-center justify-between gap-4 bg-slate-900/40 p-4 rounded-2xl border border-slate-800/80">
              <div className="relative w-full md:w-96">
                <Search className="h-4 w-4 absolute left-3 top-2.5 text-slate-500" />
                <input
                  type="text"
                  placeholder="Search student by name or roll no..."
                  value={searchTerm}
                  onChange={(e) => setSearchTerm(e.target.value)}
                  className="w-full bg-slate-950 border border-slate-800 rounded-xl pl-9 pr-4 py-2 text-xs text-slate-200 focus:outline-none focus:border-indigo-500"
                />
              </div>

              <div className="flex items-center gap-1.5 bg-slate-950 p-1.5 rounded-xl border border-slate-800 overflow-x-auto w-full md:w-auto">
                <span className="text-[10px] font-mono text-slate-500 px-2 flex items-center gap-1">
                  <Filter className="h-3 w-3" /> DEPT:
                </span>
                {["ALL", "CSE", "ECE", "EEE", "MECH"].map((dept) => (
                  <button
                    key={dept}
                    onClick={() => handleDeptFilterChange(dept)}
                    className={`px-3 py-1 rounded-lg text-xs font-bold font-mono transition ${
                      selectedDeptFilter === dept
                        ? "bg-indigo-600 text-white shadow-md"
                        : "text-slate-400 hover:text-slate-200 hover:bg-slate-900"
                    }`}
                  >
                    {dept}
                  </button>
                ))}
              </div>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-12 gap-6">
              <div className="lg:col-span-4 space-y-3">
                <div className="flex items-center justify-between px-1">
                  <h3 className="text-xs font-mono font-bold text-slate-400 uppercase tracking-wider">
                    {selectedDeptFilter === "ALL" ? "All Departments" : `${selectedDeptFilter} Department`} Students
                  </h3>
                  <span className="text-[10px] font-mono text-indigo-400 bg-indigo-950 px-2 py-0.5 rounded border border-indigo-800">
                    {filteredStudents.length} Found
                  </span>
                </div>

                <div className="space-y-2.5 max-h-[680px] overflow-y-auto pr-1">
                  {filteredStudents.map((st) => {
                    const isSelected = st.id === currentStudent.id;
                    return (
                      <div
                        key={st.id}
                        onClick={() => setActiveStudentId(st.id)}
                        className={`p-3.5 rounded-2xl border transition cursor-pointer flex items-center justify-between gap-3 ${
                          isSelected
                            ? "bg-indigo-950/60 border-indigo-500/80 shadow-[0_0_20px_rgba(79,70,229,0.2)]"
                            : "bg-slate-900/40 border-slate-800/80 hover:bg-slate-800/40"
                        }`}
                      >
                        <div className="flex items-center gap-3">
                          <img
                            src={st.avatar}
                            alt={st.name}
                            className="w-10 h-10 rounded-full object-cover border border-slate-700"
                          />
                          <div>
                            <p className="text-xs font-bold text-slate-100 flex items-center gap-1.5">
                              {st.name}
                              {isSelected && <span className="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>}
                            </p>
                            <p className="text-[10px] font-mono text-indigo-300">
                              {st.id} • <span className="text-cyan-400 font-bold">{st.deptCode}</span>
                            </p>
                          </div>
                        </div>
                        <ChevronRight className={`h-4 w-4 ${isSelected ? "text-indigo-400" : "text-slate-600"}`} />
                      </div>
                    );
                  })}
                </div>
              </div>

              {currentStudent && (
                <div className="lg:col-span-8 bg-slate-900/40 border border-slate-800/80 rounded-2xl p-6 shadow-2xl flex flex-col justify-between">
                  <div>
                    <div className="flex flex-col sm:flex-row sm:items-center justify-between pb-6 border-b border-slate-800 gap-4">
                      <div className="flex items-center gap-4">
                        <img
                          src={currentStudent.avatar}
                          alt={currentStudent.name}
                          className="w-14 h-14 rounded-2xl object-cover border-2 border-indigo-500/50 shadow-md"
                        />
                        <div>
                          <h2 className="text-base font-bold text-slate-100 flex items-center gap-2">
                            {currentStudent.name}
                            <span className="text-[10px] bg-emerald-950 text-emerald-400 border border-emerald-500/30 px-2 py-0.5 rounded-full font-mono">
                              {currentStudent.overview.status}
                            </span>
                          </h2>
                          <p className="text-xs text-slate-400">{currentStudent.dept}</p>
                          <p className="text-xs font-mono text-indigo-400 mt-0.5">Roll No: {currentStudent.id}</p>
                        </div>
                      </div>

                      <div className="flex items-center gap-3 bg-slate-950 p-3 rounded-xl border border-slate-800/80 font-mono text-xs">
                        <div className="text-center px-2">
                          <span className="text-[10px] text-slate-500 block">CGPA</span>
                          <span className="font-bold text-indigo-400 text-sm">{currentStudent.overview.gpa}</span>
                        </div>
                        <div className="w-px h-6 bg-slate-800"></div>
                        <div className="text-center px-2">
                          <span className="text-[10px] text-slate-500 block">ATTENDANCE</span>
                          <span className="font-bold text-emerald-400 text-sm">{currentStudent.overview.att}</span>
                        </div>
                      </div>
                    </div>

                    <div className="flex flex-wrap items-center gap-2 py-4 border-b border-slate-800/80">
                      {[
                        { key: "academics", label: "Academics & GPA" },
                        { key: "faculty", label: "Faculty Guides" },
                        { key: "fees", label: "Fees & Clearance" },
                        { key: "placement", label: "Placements" },
                        { key: "hostel", label: "Hostel / Transport" },
                        { key: "timetable", label: "Timetable" },
                        { key: "exams", label: "Exams & Hall Tickets" }
                      ].map((f) => (
                        <button
                          key={f.key}
                          onClick={() => setActiveFolderKey(f.key)}
                          className={`flex items-center gap-1.5 px-3 py-1.5 rounded-xl text-xs font-semibold transition ${
                            activeFolderKey === f.key
                              ? "bg-indigo-600 text-white shadow-md"
                              : "bg-slate-950 text-slate-400 hover:bg-slate-800"
                          }`}
                        >
                          {activeFolderKey === f.key ? (
                            <FolderOpen className="h-3.5 w-3.5" />
                          ) : (
                            <Folder className="h-3.5 w-3.5 text-indigo-400" />
                          )}
                          {f.label}
                        </button>
                      ))}
                    </div>

                    <div className="mt-6 bg-slate-950/60 rounded-2xl border border-slate-800 p-5 min-h-[320px]">
                      {activeFolderKey === "academics" && (
                        <div className="space-y-4">
                          <div className="flex items-center justify-between border-b border-slate-800 pb-2">
                            <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2">
                              <GraduationCap className="h-4 w-4" /> Academic Performance
                            </h4>
                            <span className="text-[10px] text-slate-400 font-mono">
                              Major: {currentStudent.folders.academics.major}
                            </span>
                          </div>
                          <div className="grid grid-cols-2 md:grid-cols-4 gap-3">
                            {currentStudent.folders.academics.cgpaHistory.map((sem, i) => (
                              <div key={i} className="bg-slate-900 p-3 rounded-xl border border-slate-800 text-center">
                                <p className="text-[10px] text-slate-400 font-mono">{sem.sem}</p>
                                <p className="text-base font-bold text-indigo-400 font-mono mt-1">{sem.gpa}</p>
                              </div>
                            ))}
                          </div>
                        </div>
                      )}

                      {activeFolderKey === "faculty" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <UserCheck className="h-4 w-4" /> Assigned Department Faculty
                          </h4>
                          <div className="grid grid-cols-1 md:grid-cols-2 gap-3">
                            {currentStudent.folders.faculty.map((f, i) => (
                              <div key={i} className="p-3.5 bg-slate-900 rounded-xl border border-slate-800 space-y-1">
                                <span className="text-[10px] font-mono text-indigo-400 font-bold bg-indigo-950 px-2 py-0.5 rounded border border-indigo-800">
                                  {f.role}
                                </span>
                                <p className="text-xs font-bold text-slate-200 mt-1">{f.name}</p>
                                <p className="text-[11px] text-slate-400 font-mono">Cabin: {f.cabin}</p>
                                <p className="text-[10px] text-cyan-400 font-mono">{f.email}</p>
                              </div>
                            ))}
                          </div>
                        </div>
                      )}

                      {activeFolderKey === "fees" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <CreditCard className="h-4 w-4" /> Financial Clearance Status
                          </h4>
                          <div className="grid grid-cols-2 gap-3 text-xs">
                            <div className="bg-slate-900 p-3 rounded-xl border border-slate-800">
                              <span className="text-slate-400 text-[10px]">Tuition Fee</span>
                              <p className="font-bold text-slate-200 font-mono mt-1">
                                {currentStudent.folders.fees.tuitionFee}
                              </p>
                            </div>
                            <div className="bg-slate-900 p-3 rounded-xl border border-slate-800">
                              <span className="text-slate-400 text-[10px]">Receipt No</span>
                              <p className="font-bold text-emerald-400 font-mono mt-1">
                                {currentStudent.folders.fees.receiptNo}
                              </p>
                            </div>
                          </div>
                        </div>
                      )}

                      {activeFolderKey === "placement" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <Briefcase className="h-4 w-4" /> Career & Placement Record
                          </h4>
                          <div className="p-3.5 bg-slate-900 rounded-xl border border-slate-800 text-xs space-y-2">
                            <p className="text-slate-400">
                              Status: <strong className="text-amber-400">{currentStudent.folders.placement.eligibility}</strong>
                            </p>
                            {currentStudent.folders.placement.offers.map((off, i) => (
                              <div key={i} className="p-2.5 bg-emerald-950/40 rounded-lg border border-emerald-500/30">
                                <p className="font-bold text-emerald-300">{off.company}</p>
                                <p className="text-slate-300 text-[11px]">
                                  {off.role} • <strong className="text-white">{off.package}</strong>
                                </p>
                              </div>
                            ))}
                          </div>
                        </div>
                      )}

                      {activeFolderKey === "hostel" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <Building className="h-4 w-4" /> Accommodation & Transport
                          </h4>
                          <div className="p-4 bg-slate-900 rounded-xl border border-slate-800 space-y-2 text-xs">
                            <p className="text-slate-400">
                              Type: <strong className="text-indigo-300">{currentStudent.folders.hostel.type}</strong>
                            </p>
                            {currentStudent.folders.hostel.type === "Hosteller" ? (
                              <p className="text-slate-400">
                                Room: <strong className="text-slate-200">{currentStudent.folders.hostel.room}</strong>
                              </p>
                            ) : (
                              <p className="text-slate-400">
                                Route: <strong className="text-slate-200">{currentStudent.folders.hostel.transportRoute}</strong>
                              </p>
                            )}
                          </div>
                        </div>
                      )}

                      {activeFolderKey === "timetable" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <Clock className="h-4 w-4" /> Weekly Class Schedule
                          </h4>
                          <table className="w-full text-left text-xs text-slate-400 font-mono">
                            <thead className="bg-slate-900 text-slate-300 uppercase text-[10px]">
                              <tr>
                                <th className="p-2">Time</th>
                                <th className="p-2">Monday</th>
                                <th className="p-2">Tuesday</th>
                              </tr>
                            </thead>
                            <tbody className="divide-y divide-slate-800">
                              {currentStudent.folders.timetable.map((r, i) => (
                                <tr key={i}>
                                  <td className="p-2 text-indigo-300">{r.time}</td>
                                  <td className="p-2 text-slate-200">{r.mon}</td>
                                  <td className="p-2 text-slate-200">{r.tue}</td>
                                </tr>
                              ))}
                            </tbody>
                          </table>
                        </div>
                      )}

                      {activeFolderKey === "exams" && (
                        <div className="space-y-4">
                          <h4 className="text-xs font-mono font-bold text-indigo-300 uppercase flex items-center gap-2 border-b border-slate-800 pb-2">
                            <Calendar className="h-4 w-4" /> CAT/FAT Exam Tickets
                          </h4>
                          {currentStudent.folders.exams.map((ex, i) => (
                            <div key={i} className="p-3 bg-slate-900 rounded-xl border border-slate-800 flex justify-between text-xs font-mono">
                              <div>
                                <span className="text-indigo-400 font-bold">{ex.code}</span>
                                <p className="text-slate-200 font-sans">{ex.subject}</p>
                              </div>
                              <div className="text-right">
                                <span className="text-cyan-300">{ex.hall}</span>
                                <p className="text-amber-400 text-[10px]">Seat: {ex.seat}</p>
                              </div>
                            </div>
                          ))}
                        </div>
                      )}
                    </div>
                  </div>

                  <div className="mt-4 pt-3 border-t border-slate-800/80 flex items-center justify-between text-[11px] text-slate-500">
                    <span>
                      Selected Department: <strong className="text-indigo-400 font-mono">{currentStudent.deptCode}</strong>
                    </span>
                    <span>AegisCampus Database v2.6</span>
                  </div>
                </div>
              )}
            </div>
          </div>
        )}

        {/* TAB 2: QR PASS MAKER */}
        {activeTab === "qrpass" && (
          <div className="grid grid-cols-1 lg:grid-cols-12 gap-6">
            <div className="lg:col-span-5 bg-slate-900/40 border border-slate-800/80 rounded-2xl p-6 shadow-2xl space-y-5">
              <div className="border-b border-slate-800 pb-3 flex items-center justify-between">
                <div>
                  <h3 className="text-sm font-bold text-slate-100 flex items-center gap-2">
                    <PlusCircle className="h-4 w-4 text-indigo-400" /> Digital Gate Pass Generator
                  </h3>
                  <p className="text-[11px] text-slate-400">Issue instant QR outpasses for hostel & campus exit</p>
                </div>
                <Sparkles className="h-4 w-4 text-amber-400 animate-pulse" />
              </div>

              <form onSubmit={handleGeneratePass} className="space-y-4 text-xs">
                <div>
                  <label className="block text-slate-400 mb-1">Select Student Record</label>
                  <select
                    value={activeStudentId}
                    onChange={(e) => setActiveStudentId(e.target.value)}
                    className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 focus:outline-none focus:border-indigo-500 font-mono"
                  >
                    {studentFolderDb.map((st) => (
                      <option key={st.id} value={st.id}>
                        [{st.deptCode}] {st.name} ({st.id})
                      </option>
                    ))}
                  </select>
                </div>

                <div>
                  <label className="block text-slate-400 mb-1">Pass Category</label>
                  <select
                    value={newPassType}
                    onChange={(e) => setNewPassType(e.target.value)}
                    className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 focus:outline-none focus:border-indigo-500"
                  >
                    <option value="Weekend Outing Pass">Weekend Outing Pass</option>
                    <option value="Emergency Outpass">Emergency Outpass</option>
                    <option value="Day Scholar Gate Clearance">Day Scholar Gate Clearance</option>
                  </select>
                </div>

                <div>
                  <label className="block text-slate-400 mb-1">Destination Address</label>
                  <input
                    type="text"
                    required
                    placeholder="e.g. T. Nagar / Airport"
                    value={newPassDestination}
                    onChange={(e) => setNewPassDestination(e.target.value)}
                    className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 focus:outline-none focus:border-indigo-500"
                  />
                </div>

                <div className="grid grid-cols-2 gap-3">
                  <div>
                    <label className="block text-slate-400 mb-1">Exit Time</label>
                    <input
                      type="text"
                      value={newPassOutTime}
                      onChange={(e) => setNewPassOutTime(e.target.value)}
                      className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 font-mono focus:outline-none focus:border-indigo-500"
                    />
                  </div>
                  <div>
                    <label className="block text-slate-400 mb-1">Return Time</label>
                    <input
                      type="text"
                      value={newPassInTime}
                      onChange={(e) => setNewPassInTime(e.target.value)}
                      className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 font-mono focus:outline-none focus:border-indigo-500"
                    />
                  </div>
                </div>

                <div>
                  <label className="block text-slate-400 mb-1">Reason for Leave</label>
                  <textarea
                    rows="3"
                    required
                    placeholder="Provide specific reason for campus departure..."
                    value={newPassReason}
                    onChange={(e) => setNewPassReason(e.target.value)}
                    className="w-full bg-slate-950 border border-slate-800 rounded-xl p-2.5 text-slate-200 focus:outline-none focus:border-indigo-500"
                  ></textarea>
                </div>

                <button
                  type="submit"
                  className="w-full py-3 bg-gradient-to-r from-indigo-600 to-indigo-700 hover:from-indigo-500 hover:to-indigo-600 text-white font-bold rounded-xl shadow-lg transition flex items-center justify-center gap-2"
                >
                  <QrCode className="h-4 w-4" /> GENERATE & SIGN DIGITAL PASS
                </button>
              </form>
            </div>

            <div className="lg:col-span-7 space-y-4">
              <h3 className="text-xs font-mono font-bold text-slate-400 uppercase tracking-wider px-1">
                Active Gate Passes ({passList.length})
              </h3>

              <div className="space-y-4 max-h-[650px] overflow-y-auto pr-1">
                {passList.map((p, idx) => (
                  <div
                    key={idx}
                    className="bg-slate-900/60 border border-slate-800 rounded-2xl p-5 shadow-xl relative overflow-hidden"
                  >
                    <div className="flex flex-col sm:flex-row sm:items-center justify-between border-b border-slate-800 pb-3 gap-2">
                      <div>
                        <span className="text-[10px] font-mono text-indigo-400 font-bold bg-indigo-950 px-2 py-0.5 rounded border border-indigo-800/80">
                          {p.passId}
                        </span>
                        <h4 className="text-sm font-bold text-slate-100 mt-1">{p.studentName}</h4>
                        <p className="text-[11px] text-slate-400 font-mono">Roll: {p.studentId}</p>
                      </div>

                      <span className="px-2.5 py-1 rounded-full text-[10px] font-bold bg-emerald-950 text-emerald-400 border border-emerald-500/30 flex items-center gap-1 font-mono">
                        <CheckCircle2 className="h-3 w-3" /> {p.status}
                      </span>
                    </div>

                    <div className="grid grid-cols-1 md:grid-cols-3 gap-4 mt-4">
                      <div className="md:col-span-2 space-y-1.5 text-xs">
                        <p className="text-slate-400">
                          Category: <strong className="text-slate-200">{p.type}</strong>
                        </p>
                        <p className="text-slate-400">
                          Departure: <strong className="text-emerald-400 font-mono">{p.outTime}</strong>
                        </p>
                        <p className="text-slate-400">
                          Expected In: <strong className="text-cyan-400 font-mono">{p.inTime}</strong>
                        </p>
                        <p className="text-slate-400">
                          Destination: <strong className="text-slate-200">{p.destination}</strong>
                        </p>
                        <p className="text-slate-400">
                          Reason: <strong className="text-slate-300">{p.reason}</strong>
                        </p>
                      </div>

                      <div className="bg-slate-950 p-3 rounded-xl border border-slate-800 flex flex-col items-center justify-center text-center space-y-2">
                        <div className="bg-white p-2 rounded-lg shadow-md">
                          <QrCode className="h-16 w-16 text-slate-950" />
                        </div>
                        <span className="text-[9px] font-mono text-indigo-300">{p.qrToken}</span>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {/* TAB 3: FIXED EMERGENCY RADAR WITH LIVE HELP STATUS TRACKER */}
        {activeTab === "safety" && (
          <div className="space-y-6">
            <div className="bg-slate-900/40 backdrop-blur-xl border border-slate-800/80 rounded-2xl p-6 shadow-2xl space-y-4">
              <div className="flex items-center justify-between">
                <div>
                  <h3 className="text-sm font-bold text-slate-200">Live Campus Emergency Radar</h3>
                  <p className="text-[11px] text-slate-400 font-mono">Custom Blueprint Layout</p>
                </div>
                <span className="text-xs text-indigo-400 font-mono bg-indigo-950/80 px-3 py-1 rounded-full border border-indigo-800">
                  {incidents.length} Active SOS Signals
                </span>
              </div>

              {/* Vector Map Display (Hover-jump motion bug fixed) */}
              <div className="relative w-full aspect-[16/9] max-h-[520px] bg-slate-950 border border-slate-800 rounded-xl overflow-hidden p-2">
                <svg className="w-full h-full" viewBox="0 0 900 500" preserveAspectRatio="xMidYMid meet">
                  <rect width="900" height="500" fill="#020617" />

                  {/* CONNECTING ROADS FROM SKETCH */}
                  <path d="M 180,60 L 180,420" stroke="#334155" strokeWidth="4" strokeDasharray="6,4" />
                  <path d="M 180,420 L 520,420 L 520,380" stroke="#334155" strokeWidth="4" strokeDasharray="6,4" />
                  <path d="M 180,90 L 320,90" stroke="#334155" strokeWidth="4" />
                  <path d="M 380,120 L 380,150" stroke="#334155" strokeWidth="4" />
                  <path d="M 380,210 C 380,260 480,220 480,270" stroke="#334155" strokeWidth="4" />
                  <path d="M 480,330 L 480,360 L 620,360" stroke="#334155" strokeWidth="4" />
                  <path d="M 440,90 L 680,90 L 680,360" stroke="#334155" strokeWidth="4" />
                  <path d="M 440,180 C 560,180 560,250 680,250" stroke="#334155" strokeWidth="3" strokeDasharray="4,4" />

                  {/* GATES */}
                  <g transform="translate(180, 90)">
                    <line x1="-12" y1="-10" x2="-12" y2="10" stroke="#f59e0b" strokeWidth="3" />
                    <line x1="12" y1="-10" x2="12" y2="10" stroke="#f59e0b" strokeWidth="3" />
                    <text x="-25" y="4" fill="#f59e0b" fontSize="12" fontWeight="bold" fontFamily="monospace">
                      Gate 3
                    </text>
                  </g>

                  <g transform="translate(180, 240)">
                    <line x1="-10" y1="-12" x2="10" y2="-12" stroke="#f59e0b" strokeWidth="3" />
                    <line x1="-10" y1="12" x2="10" y2="12" stroke="#f59e0b" strokeWidth="3" />
                    <text x="-65" y="4" fill="#f59e0b" fontSize="12" fontWeight="bold" fontFamily="monospace">
                      Gate 1
                    </text>
                  </g>

                  <g transform="translate(380, 420)">
                    <line x1="-10" y1="-12" x2="10" y2="-12" stroke="#f59e0b" strokeWidth="3" />
                    <line x1="-10" y1="12" x2="10" y2="12" stroke="#f59e0b" strokeWidth="3" />
                    <text x="-22" y="28" fill="#f59e0b" fontSize="12" fontWeight="bold" fontFamily="monospace">
                      Gate 2
                    </text>
                  </g>

                  {/* BLOCKS */}
                  <g transform="translate(320, 60)">
                    <rect width="120" height="60" rx="8" fill="#0f172a" stroke="#6366f1" strokeWidth="2.5" />
                    <text x="60" y="35" fill="#e2e8f0" fontSize="13" fontWeight="bold" textAnchor="middle">
                      D Block
                    </text>
                  </g>

                  <g transform="translate(620, 60)">
                    <rect width="120" height="60" rx="8" fill="#0f172a" stroke="#38bdf8" strokeWidth="2.5" />
                    <text x="60" y="35" fill="#e2e8f0" fontSize="13" fontWeight="bold" textAnchor="middle">
                      C Block
                    </text>
                  </g>

                  <g transform="translate(320, 150)">
                    <rect width="120" height="60" rx="8" fill="#1e1b4b" stroke="#818cf8" strokeWidth="2.5" />
                    <text x="60" y="35" fill="#e0e7ff" fontSize="14" fontWeight="bold" textAnchor="middle">
                      AB-1
                    </text>
                  </g>

                  <g transform="translate(420, 270)">
                    <rect width="120" height="60" rx="8" fill="#0f172a" stroke="#6366f1" strokeWidth="2.5" />
                    <text x="60" y="35" fill="#e2e8f0" fontSize="14" fontWeight="bold" textAnchor="middle">
                      AB-2
                    </text>
                  </g>

                  <g transform="translate(620, 320)">
                    <rect width="140" height="80" rx="10" fill="#022c22" stroke="#10b981" strokeWidth="2.5" />
                    <text x="70" y="38" fill="#a7f3d0" fontSize="13" fontWeight="bold" textAnchor="middle">
                      Medical
                    </text>
                    <text x="70" y="56" fill="#a7f3d0" fontSize="13" fontWeight="bold" textAnchor="middle">
                      Center
                    </text>
                  </g>

                  {/* FIXED SOS DOTS (No scale transforms on hover to prevent moving/jumping) */}
                  {incidents.map((inc) => (
                    <g
                      key={inc.id}
                      transform={`translate(${inc.coords.x}, ${inc.coords.y})`}
                      className="cursor-pointer"
                      onClick={() => setSelectedMapIncident(inc)}
                    >
                      <circle r="20" fill="#ef4444" fillOpacity="0.3" className="animate-ping" />
                      <circle r="9" fill="#ef4444" stroke="#ffffff" strokeWidth="2" />
                    </g>
                  ))}
                </svg>
              </div>
            </div>

            {/* LIVE HELP DISPATCH STATUS PANEL */}
            <div className="bg-slate-900/40 border border-slate-800/80 rounded-2xl p-6 shadow-2xl space-y-4">
              <div className="flex items-center justify-between border-b border-slate-800 pb-3">
                <h4 className="text-xs font-mono font-bold text-slate-200 uppercase flex items-center gap-2">
                  <Radio className="h-4 w-4 text-emerald-400 animate-pulse" /> Security Patrol & Emergency Dispatch Tracker
                </h4>
                <span className="text-[10px] font-mono text-slate-400">Real-Time Sync active</span>
              </div>

              <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                {incidents.map((inc) => (
                  <div
                    key={inc.id}
                    className="bg-slate-950 p-4 rounded-xl border border-slate-800/90 space-y-3 relative overflow-hidden"
                  >
                    <div className="flex items-center justify-between border-b border-slate-800/60 pb-2">
                      <div>
                        <span className="text-[10px] font-mono text-red-400 font-bold bg-red-950/80 px-2 py-0.5 rounded border border-red-800/50">
                          {inc.type}
                        </span>
                        <h5 className="text-xs font-bold text-slate-100 mt-1">{inc.locName}</h5>
                      </div>
                      <div className="text-right font-mono">
                        <span className="text-[10px] text-slate-500 block">ETA</span>
                        <span className="text-xs font-bold text-emerald-400">{inc.eta}</span>
                      </div>
                    </div>

                    <div className="space-y-1.5 text-xs font-mono">
                      <p className="text-slate-400 text-[11px]">
                        Responder: <strong className="text-indigo-300">{inc.responder}</strong>
                      </p>
                      <p className="text-slate-400 text-[11px]">
                        Status: <strong className="text-cyan-400">{inc.statusText}</strong>
                      </p>
                    </div>

                    {/* Progress Bar for Help Status */}
                    <div className="space-y-1 pt-1">
                      <div className="flex justify-between text-[9px] font-mono text-slate-500">
                        <span className={inc.statusStage >= 0 ? "text-amber-400 font-bold" : ""}>Received</span>
                        <span className={inc.statusStage >= 1 ? "text-indigo-400 font-bold" : ""}>En Route</span>
                        <span className={inc.statusStage >= 2 ? "text-emerald-400 font-bold" : ""}>On Scene</span>
                      </div>
                      <div className="w-full h-1.5 bg-slate-900 rounded-full overflow-hidden border border-slate-800 flex">
                        <div
                          className={`h-full transition-all duration-500 ${
                            inc.statusStage === 0
                              ? "w-1/3 bg-amber-500"
                              : inc.statusStage === 1
                              ? "w-2/3 bg-indigo-500"
                              : "w-full bg-emerald-500"
                          }`}
                        ></div>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}
      </main>
    </div>
  );
}
