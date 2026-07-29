---
title: Database Schema Example for IT Business
description: 
published: true
date: 2026-07-29T21:42:36.536Z
tags: mysql, schema, it, it support
editor: markdown
dateCreated: 2026-07-29T21:42:36.536Z
---

```mysql
-- Create database
CREATE DATABASE pc_repair_service;
USE pc_repair_service;

-- Customers table
CREATE TABLE customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    phone VARCHAR(20),
    address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Devices table
CREATE TABLE devices (
    device_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    device_type VARCHAR(50),   -- e.g., Laptop, Desktop, Server
    brand VARCHAR(50),
    model VARCHAR(100),
    serial_number VARCHAR(100) UNIQUE,
    notes TEXT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE
);

-- Work Orders table
CREATE TABLE work_orders (
    work_order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    device_id INT NOT NULL,
    status ENUM('Pending','In Progress','Completed','Cancelled') DEFAULT 'Pending',
    issue_description TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    completed_at TIMESTAMP NULL,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE,
    FOREIGN KEY (device_id) REFERENCES devices(device_id) ON DELETE CASCADE
);

-- Services/Tasks for each work order
CREATE TABLE services (
    service_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,   -- e.g., Virus Removal, Data Backup
    description TEXT,
    base_price DECIMAL(10,2)
);

-- Work order services (many-to-many)
CREATE TABLE work_order_services (
    work_order_id INT,
    service_id INT,
    cost DECIMAL(10,2),
    PRIMARY KEY (work_order_id, service_id),
    FOREIGN KEY (work_order_id) REFERENCES work_orders(work_order_id) ON DELETE CASCADE,
    FOREIGN KEY (service_id) REFERENCES services(service_id) ON DELETE CASCADE
);

-- Service schedule / appointments
CREATE TABLE schedules (
    schedule_id INT AUTO_INCREMENT PRIMARY KEY,
    work_order_id INT NOT NULL,
    scheduled_date DATETIME NOT NULL,
    estimated_completion DATETIME,
    status ENUM('Scheduled','Ongoing','Completed','Rescheduled','Cancelled') DEFAULT 'Scheduled',
    FOREIGN KEY (work_order_id) REFERENCES work_orders(work_order_id) ON DELETE CASCADE
);

-- Invoices table
CREATE TABLE invoices (
    invoice_id INT AUTO_INCREMENT PRIMARY KEY,
    work_order_id INT NOT NULL,
    total_amount DECIMAL(10,2) NOT NULL,
    paid_amount DECIMAL(10,2) DEFAULT 0.00,
    status ENUM('Unpaid','Partially Paid','Paid') DEFAULT 'Unpaid',
    issued_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    due_date DATE,
    FOREIGN KEY (work_order_id) REFERENCES work_orders(work_order_id) ON DELETE CASCADE
);

-- Payments table (for multiple payments per invoice)
CREATE TABLE payments (
    payment_id INT AUTO_INCREMENT PRIMARY KEY,
    invoice_id INT NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    payment_method VARCHAR(50), -- Cash, Card, Online
    paid_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (invoice_id) REFERENCES invoices(invoice_id) ON DELETE CASCADE
);

-- Populate services table with Basic PC Repair services with description and price 
INSERT INTO services (name, description, base_price) VALUES
('Diagnostics', 'Full system diagnostic to identify issues', 30.00),
('Virus Removal', 'Scan and remove viruses/malware', 60.00),
('Data Backup', 'Backup important files before repair', 50.00),
('Operating System Reinstall', 'Reinstall Windows/Linux/macOS with updates', 80.00),
('Hardware Replacement', 'Replace faulty hardware (RAM, HDD, SSD, GPU, PSU, etc.)', 0.00),
('SSD Upgrade', 'Replace HDD with SSD, includes cloning or fresh OS install', 120.00),
('Data Migration', 'Migrate data to new system or when upgrading storage devices', 50.00),
('Laptop Screen Replacement', 'Replace cracked or faulty laptop screen', 200.00),
('Keyboard Replacement', 'Replace damaged or faulty keyboard', 100.00),
('Battery Replacement', 'Replace laptop battery', 90.00),
('Thermal Paste & Cleaning', 'Disassemble, clean dust, replace thermal paste', 70.00),
('Network Troubleshooting', 'Fix internet or LAN connectivity issues', 50.00),
('Software Installation', 'Install requested applications/software', 40.00),
('System Optimization', 'Remove unwanted programs, manage background tasks, limit startup apps etc.', 25.00);
```

