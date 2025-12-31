# RDF (RecoverDeletedFiles)

This application is designed to recover deleted files from storage devices.

## Overview
RDF (RecoverDeletedFiles) is a file recovery tool that helps users restore files that have been accidentally deleted from their storage devices. The application works by scanning storage devices at the raw sector level to identify file signatures and recover deleted files based on their file headers. (the current running version is 1.0a)

## How It Works

### Core Components

The application consists of three main components:

1. **File Recovery Engine**: The core component that performs low-level scanning of storage devices to identify and recover deleted files based on file signatures.

2. **USB Drive Detector**: Identifies and validates removable storage devices, particularly USB drives, that can be scanned for deleted files.

3. **Main Application Window**: Provides the user interface for selecting drives, scanning for files, and recovering them.

### File Recovery Process

The recovery process works by:

1. **Device Detection**: The application scans for available removable drives using the DriveInfo class and validates if they are USB devices through registry checks.

2. **Raw Data Scanning**: The application accesses drives at a low level using Windows API calls (CreateFile, ReadFile) to read raw sectors without relying on the file system.

3. **File Signature Recognition**: The engine identifies potential files by looking for known file signatures (magic numbers) in the raw data. These signatures include patterns for common file types like JPG, PNG, GIF, PDF, ZIP, DOC, DOCX, XLS, XLSX, MP4, MP3, and others.

4. **File Reconstruction**: Once a file signature is found, the application estimates the file size and creates a recoverable file entry with its location on the storage device.

5. **Recovery Operation**: When a user selects a file to recover, the application reads the raw data from the device at the identified location and writes it to a new file at the user-specified destination.

### Supported File Types

The application currently supports recovery of the following file types based on their signatures:
- Image files: JPG, PNG, GIF
- Document files: PDF, DOC, DOCX, XLS, XLSX
- Archive files: ZIP, RAR
- Media files: MP4, MP3, AVI
- Other: TXT, EXE, DLL

### User Interface

The application provides a Windows desktop interface with:
- Drive selection dropdown
- Scan controls with progress indication
- File listing with file type and size information
- File preview capabilities
- Recovery controls

## Features
- Scan storage devices for recoverable files at the raw sector level
- Support for multiple file types based on signature recognition
- Preview files before recovery
- Recover files to a specified location
- Progress tracking during scanning operations

## Usage
1. Connect the storage device you want to scan
2. Launch the application
3. Select the storage device from the dropdown
4. Click "Scan for Deleted Files" to start the scan process
5. Review the list of found files in the file list
6. Select a file to see preview information
7. Click "Recover Selected File" to save the file to your chosen location
