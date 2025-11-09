# prashant-student-management-system<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>University Student Management System</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --success: #2ecc71;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
        }
        
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar Styles */
        .sidebar {
            width: 250px;
            background: var(--secondary);
            color: white;
            transition: all 0.3s;
            box-shadow: 3px 0 10px rgba(0, 0, 0, 0.1);
        }
        
        .sidebar-header {
            padding: 20px;
            background: var(--primary);
            text-align: center;
        }
        
        .sidebar-header h2 {
            font-size: 1.5rem;
            margin-bottom: 5px;
        }
        
        .sidebar-menu {
            padding: 15px 0;
        }
        
        .sidebar-menu ul {
            list-style: none;
        }
        
        .sidebar-menu li {
            padding: 12px 20px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
        }
        
        .sidebar-menu li:hover {
            background: rgba(255, 255, 255, 0.1);
        }
        
        .sidebar-menu li.active {
            background: var(--primary);
            border-left: 4px solid white;
        }
        
        .sidebar-menu li i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }
        
        /* Main Content Styles */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #ddd;
        }
        
        .header h1 {
            color: var(--secondary);
            font-size: 1.8rem;
        }
        
        .user-info {
            display: flex;
            align-items: center;
        }
        
        .user-info img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .card h3 {
            color: var(--secondary);
            margin-bottom: 10px;
            font-size: 1.1rem;
        }
        
        .card .number {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
        }
        
        /* Table Styles */
        .table-container {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background: var(--light);
            font-weight: 600;
            color: var(--secondary);
        }
        
        tr:hover {
            background: #f9f9f9;
        }
        
        /* Form Styles */
        .form-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background 0.3s;
        }
        
        button:hover {
            background: #2980b9;
        }
        
        .btn-danger {
            background: var(--danger);
        }
        
        .btn-danger:hover {
            background: #c0392b;
        }
        
        .btn-success {
            background: var(--success);
        }
        
        .btn-success:hover {
            background: #27ae60;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: 600;
        }
        
        /* Attendance Status */
        .attendance-status {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        
        .present {
            background: #d4edda;
            color: #155724;
        }
        
        .absent {
            background: #f8d7da;
            color: #721c24;
        }
        
        .late {
            background: #fff3cd;
            color: #856404;
        }
        
        /* Timetable */
        .timetable {
            display: grid;
            grid-template-columns: 100px repeat(5, 1fr);
            gap: 1px;
            background: #ddd;
            border-radius: 8px;
            overflow: hidden;
        }
        
        .timetable-cell {
            background: white;
            padding: 15px;
            min-height: 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .timetable-header {
            background: var(--secondary);
            color: white;
            font-weight: 600;
            text-align: center;
        }
        
        .subject {
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .time {
            font-size: 0.8rem;
            color: #666;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
            }
            
            .dashboard-cards {
                grid-template-columns: 1fr;
            }
            
            .timetable {
                grid-template-columns: 80px repeat(5, 1fr);
                font-size: 0.8rem;
            }
            
            .timetable-cell {
                padding: 8px;
                min-height: 60px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="sidebar-header">
                <h2>University Portal</h2>
                <p>Student Management System</p>
            </div>
            <div class="sidebar-menu">
                <ul>
                    <li class="active" data-tab="dashboard"><i>📊</i> Dashboard</li>
                    <li data-tab="students"><i>👨‍🎓</i> Students</li>
                    <li data-tab="attendance"><i>📅</i> Attendance</li>
                    <li data-tab="timetable"><i>📚</i> Timetable</li>
                    <li data-tab="courses"><i>📖</i> Courses</li>
                    <li data-tab="grades"><i>📝</i> Grades</li>
                    <li data-tab="settings"><i>⚙️</i> Settings</li>
                </ul>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <h1>Dashboard</h1>
                <div class="user-info">
                    <img src="https://ui-avatars.com/api/?name=Admin+User&background=3498db&color=fff" alt="Admin User">
                    <span>Admin User</span>
                </div>
            </div>
            
            <!-- Dashboard Content -->
            <div id="dashboard" class="tab-content active">
                <div class="dashboard-cards">
                    <div class="card">
                        <h3>Total Students</h3>
                        <div class="number">1,254</div>
                        <p>Registered in the system</p>
                    </div>
                    <div class="card">
                        <h3>Today's Attendance</h3>
                        <div class="number">87%</div>
                        <p>Present: 1,091 / Absent: 163</p>
                    </div>
                    <div class="card">
                        <h3>Active Courses</h3>
                        <div class="number">42</div>
                        <p>Across all departments</p>
                    </div>
                    <div class="card">
                        <h3>Pending Tasks</h3>
                        <div class="number">12</div>
                        <p>Require attention</p>
                    </div>
                </div>
                
                <div class="table-container">
                    <h3 style="padding: 15px 20px 0;">Recent Activity</h3>
                    <table>
                        <thead>
                            <tr>
                                <th>Student</th>
                                <th>Activity</th>
                                <th>Date & Time</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>John Smith</td>
                                <td>Submitted Assignment - CS101</td>
                                <td>2023-10-15 14:30</td>
                                <td><span class="attendance-status present">Completed</span></td>
                            </tr>
                            <tr>
                                <td>Sarah Johnson</td>
                                <td>Requested Grade Review</td>
                                <td>2023-10-15 13:45</td>
                                <td><span class="attendance-status late">Pending</span></td>
                            </tr>
                            <tr>
                                <td>Michael Brown</td>
                                <td>Attendance Marked Absent</td>
                                <td>2023-10-15 10:15</td>
                                <td><span class="attendance-status absent">Notified</span></td>
                            </tr>
                            <tr>
                                <td>Emily Davis</td>
                                <td>Course Registration</td>
                                <td>2023-10-14 16:20</td>
                                <td><span class="attendance-status present">Approved</span></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Students Content -->
            <div id="students" class="tab-content">
                <div class="header">
                    <h1>Student Management</h1>
                    <button>Add New Student</button>
                </div>
                
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Name</th>
                                <th>Email</th>
                                <th>Course</th>
                                <th>Year</th>
                                <th>Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>S001</td>
                                <td>John Smith</td>
                                <td>john.smith@university.edu</td>
                                <td>Computer Science</td>
                                <td>3rd Year</td>
                                <td><span class="attendance-status present">Active</span></td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S002</td>
                                <td>Sarah Johnson</td>
                                <td>sarah.j@university.edu</td>
                                <td>Business Administration</td>
                                <td>2nd Year</td>
                                <td><span class="attendance-status present">Active</span></td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S003</td>
                                <td>Michael Brown</td>
                                <td>m.brown@university.edu</td>
                                <td>Electrical Engineering</td>
                                <td>4th Year</td>
                                <td><span class="attendance-status absent">Inactive</span></td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S004</td>
                                <td>Emily Davis</td>
                                <td>emily.davis@university.edu</td>
                                <td>Psychology</td>
                                <td>1st Year</td>
                                <td><span class="attendance-status present">Active</span></td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Attendance Content -->
            <div id="attendance" class="tab-content">
                <div class="header">
                    <h1>Attendance Management</h1>
                    <div>
                        <input type="date" style="width: auto; margin-right: 10px;">
                        <button>Mark Attendance</button>
                    </div>
                </div>
                
                <div class="tabs">
                    <div class="tab active">Today (Oct 15, 2023)</div>
                    <div class="tab">This Week</div>
                    <div class="tab">This Month</div>
                </div>
                
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Student ID</th>
                                <th>Name</th>
                                <th>Course</th>
                                <th>9:00 AM</th>
                                <th>11:00 AM</th>
                                <th>2:00 PM</th>
                                <th>Overall</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>S001</td>
                                <td>John Smith</td>
                                <td>Computer Science</td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status late">Late</span></td>
                                <td><span class="attendance-status present">87%</span></td>
                            </tr>
                            <tr>
                                <td>S002</td>
                                <td>Sarah Johnson</td>
                                <td>Business Administration</td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status absent">Absent</span></td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status late">75%</span></td>
                            </tr>
                            <tr>
                                <td>S003</td>
                                <td>Michael Brown</td>
                                <td>Electrical Engineering</td>
                                <td><span class="attendance-status absent">Absent</span></td>
                                <td><span class="attendance-status absent">Absent</span></td>
                                <td><span class="attendance-status absent">Absent</span></td>
                                <td><span class="attendance-status absent">45%</span></td>
                            </tr>
                            <tr>
                                <td>S004</td>
                                <td>Emily Davis</td>
                                <td>Psychology</td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status present">Present</span></td>
                                <td><span class="attendance-status present">95%</span></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Timetable Content -->
            <div id="timetable" class="tab-content">
                <div class="header">
                    <h1>Class Timetable</h1>
                    <div>
                        <select style="width: auto; margin-right: 10px;">
                            <option>Computer Science - Year 3</option>
                            <option>Business Administration - Year 2</option>
                            <option>Electrical Engineering - Year 4</option>
                            <option>Psychology - Year 1</option>
                        </select>
                        <button>Export</button>
                    </div>
                </div>
                
                <div class="timetable">
                    <div class="timetable-cell timetable-header">Time</div>
                    <div class="timetable-cell timetable-header">Monday</div>
                    <div class="timetable-cell timetable-header">Tuesday</div>
                    <div class="timetable-cell timetable-header">Wednesday</div>
                    <div class="timetable-cell timetable-header">Thursday</div>
                    <div class="timetable-cell timetable-header">Friday</div>
                    
                    <div class="timetable-cell timetable-header">9:00-10:30</div>
                    <div class="timetable-cell">
                        <div class="subject">Data Structures</div>
                        <div class="time">Room 201</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Algorithms</div>
                        <div class="time">Room 305</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Database Systems</div>
                        <div class="time">Lab 102</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Web Development</div>
                        <div class="time">Lab 105</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Software Engineering</div>
                        <div class="time">Room 201</div>
                    </div>
                    
                    <div class="timetable-cell timetable-header">11:00-12:30</div>
                    <div class="timetable-cell">
                        <div class="subject">Computer Networks</div>
                        <div class="time">Room 305</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Operating Systems</div>
                        <div class="time">Room 201</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Data Structures</div>
                        <div class="time">Room 201</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Algorithms</div>
                        <div class="time">Room 305</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Database Systems</div>
                        <div class="time">Lab 102</div>
                    </div>
                    
                    <div class="timetable-cell timetable-header">2:00-3:30</div>
                    <div class="timetable-cell">
                        <div class="subject">Web Development</div>
                        <div class="time">Lab 105</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Software Engineering</div>
                        <div class="time">Room 201</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Computer Networks</div>
                        <div class="time">Room 305</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Operating Systems</div>
                        <div class="time">Room 201</div>
                    </div>
                    <div class="timetable-cell">
                        <div class="subject">Project Work</div>
                        <div class="time">Lab 102</div>
                    </div>
                </div>
            </div>
            
            <!-- Courses Content -->
            <div id="courses" class="tab-content">
                <div class="header">
                    <h1>Course Management</h1>
                    <button>Add New Course</button>
                </div>
                
                <div class="dashboard-cards">
                    <div class="card">
                        <h3>Computer Science</h3>
                        <div class="number">15 Courses</div>
                        <p>312 Students Enrolled</p>
                    </div>
                    <div class="card">
                        <h3>Business Administration</h3>
                        <div class="number">12 Courses</div>
                        <p>285 Students Enrolled</p>
                    </div>
                    <div class="card">
                        <h3>Electrical Engineering</h3>
                        <div class="number">10 Courses</div>
                        <p>198 Students Enrolled</p>
                    </div>
                    <div class="card">
                        <h3>Psychology</h3>
                        <div class="number">8 Courses</div>
                        <p>175 Students Enrolled</p>
                    </div>
                </div>
                
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Course Code</th>
                                <th>Course Name</th>
                                <th>Department</th>
                                <th>Credits</th>
                                <th>Instructor</th>
                                <th>Enrolled</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>CS101</td>
                                <td>Introduction to Programming</td>
                                <td>Computer Science</td>
                                <td>3</td>
                                <td>Dr. James Wilson</td>
                                <td>85</td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>BA201</td>
                                <td>Principles of Management</td>
                                <td>Business Administration</td>
                                <td>3</td>
                                <td>Prof. Sarah Miller</td>
                                <td>72</td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>EE301</td>
                                <td>Circuit Analysis</td>
                                <td>Electrical Engineering</td>
                                <td>4</td>
                                <td>Dr. Robert Chen</td>
                                <td>58</td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                            <tr>
                                <td>PSY101</td>
                                <td>Introduction to Psychology</td>
                                <td>Psychology</td>
                                <td>3</td>
                                <td>Dr. Amanda Roberts</td>
                                <td>92</td>
                                <td>
                                    <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                                    <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Grades Content -->
            <div id="grades" class="tab-content">
                <div class="header">
                    <h1>Grade Management</h1>
                    <div>
                        <select style="width: auto; margin-right: 10px;">
                            <option>All Courses</option>
                            <option>Computer Science</option>
                            <option>Business Administration</option>
                            <option>Electrical Engineering</option>
                            <option>Psychology</option>
                        </select>
                        <button>Export Grades</button>
                    </div>
                </div>
                
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Student ID</th>
                                <th>Name</th>
                                <th>CS101</th>
                                <th>BA201</th>
                                <th>EE301</th>
                                <th>PSY101</th>
                                <th>GPA</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>S001</td>
                                <td>John Smith</td>
                                <td>A</td>
                                <td>B+</td>
                                <td>A-</td>
                                <td>B</td>
                                <td>3.45</td>
                                <td>
                                    <button style="padding: 5px 10px;">Edit Grades</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S002</td>
                                <td>Sarah Johnson</td>
                                <td>B+</td>
                                <td>A</td>
                                <td>B</td>
                                <td>A-</td>
                                <td>3.52</td>
                                <td>
                                    <button style="padding: 5px 10px;">Edit Grades</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S003</td>
                                <td>Michael Brown</td>
                                <td>C+</td>
                                <td>B-</td>
                                <td>C</td>
                                <td>D+</td>
                                <td>2.15</td>
                                <td>
                                    <button style="padding: 5px 10px;">Edit Grades</button>
                                </td>
                            </tr>
                            <tr>
                                <td>S004</td>
                                <td>Emily Davis</td>
                                <td>A</td>
                                <td>A-</td>
                                <td>B+</td>
                                <td>A</td>
                                <td>3.75</td>
                                <td>
                                    <button style="padding: 5px 10px;">Edit Grades</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Settings Content -->
            <div id="settings" class="tab-content">
                <div class="header">
                    <h1>System Settings</h1>
                </div>
                
                <div class="form-container">
                    <h3>General Settings</h3>
                    <div class="form-group">
                        <label for="university-name">University Name</label>
                        <input type="text" id="university-name" value="University of Technology">
                    </div>
                    <div class="form-group">
                        <label for="academic-year">Academic Year</label>
                        <input type="text" id="academic-year" value="2023-2024">
                    </div>
                    <div class="form-group">
                        <label for="semester">Current Semester</label>
                        <select id="semester">
                            <option>Fall</option>
                            <option selected>Spring</option>
                            <option>Summer</option>
                        </select>
                    </div>
                    <button class="btn-success">Save Settings</button>
                </div>
                
                <div class="form-container">
                    <h3>User Management</h3>
                    <div class="form-group">
                        <label for="admin-name">Admin Name</label>
                        <input type="text" id="admin-name" value="Admin User">
                    </div>
                    <div class="form-group">
                        <label for="admin-email">Admin Email</label>
                        <input type="email" id="admin-email" value="admin@university.edu">
                    </div>
                    <div class="form-group">
                        <label for="admin-password">Change Password</label>
                        <input type="password" id="admin-password" placeholder="Enter new password">
                    </div>
                    <button class="btn-success">Update Profile</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Tab navigation functionality
        document.querySelectorAll('.sidebar-menu li').forEach(item => {
            item.addEventListener('click', function() {
                // Remove active class from all menu items
                document.querySelectorAll('.sidebar-menu li').forEach(li => {
                    li.classList.remove('active');
                });
                
                // Add active class to clicked menu item
                this.classList.add('active');
                
                // Hide all tab content
                document.querySelectorAll('.tab-content').forEach(tab => {
                    tab.classList.remove('active');
                });
                
                // Show selected tab content
                const tabId = this.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
                
                // Update header title
                const headerTitle = document.querySelector('.header h1');
                headerTitle.textContent = this.textContent.trim();
            });
        });
        
        // Tab functionality for attendance section
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', function() {
                // Remove active class from all tabs
                document.querySelectorAll('.tab').forEach(t => {
                    t.classList.remove('active');
                });
                
                // Add active class to clicked tab
                this.classList.add('active');
            });
        });
        
        // Sample data for demonstration
        const sampleStudents = [
            { id: 'S001', name: 'John Smith', email: 'john.smith@university.edu', course: 'Computer Science', year: '3rd Year', status: 'Active' },
            { id: 'S002', name: 'Sarah Johnson', email: 'sarah.j@university.edu', course: 'Business Administration', year: '2nd Year', status: 'Active' },
            { id: 'S003', name: 'Michael Brown', email: 'm.brown@university.edu', course: 'Electrical Engineering', year: '4th Year', status: 'Inactive' },
            { id: 'S004', name: 'Emily Davis', email: 'emily.davis@university.edu', course: 'Psychology', year: '1st Year', status: 'Active' }
        ];
        
        // Function to populate student table (for demonstration)
        function populateStudentTable() {
            const tbody = document.querySelector('#students table tbody');
            tbody.innerHTML = '';
            
            sampleStudents.forEach(student => {
                const statusClass = student.status === 'Active' ? 'present' : 'absent';
                
                const row = `
                    <tr>
                        <td>${student.id}</td>
                        <td>${student.name}</td>
                        <td>${student.email}</td>
                        <td>${student.course}</td>
                        <td>${student.year}</td>
                        <td><span class="attendance-status ${statusClass}">${student.status}</span></td>
                        <td>
                            <button style="padding: 5px 10px; margin-right: 5px;">Edit</button>
                            <button class="btn-danger" style="padding: 5px 10px;">Delete</button>
                        </td>
                    </tr>
                `;
                
                tbody.innerHTML += row;
            });
        }
        
        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            populateStudentTable();
        });
    </script>
</body>
</html>
