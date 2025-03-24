# 📅 calendar-rfc5545-django-core

A standards-compliant core calendar model implementation based on **RFC 5545 (iCalendar)** and **RFC 4791 (CalDAV)** with support for:
- 🧩 iCalendar components (VEVENT, VTODO, VJOURNAL, VFREEBUSY, VTIMEZONE)
- 🧠 PUML diagrams for data modeling
- 🔁 WebDAV/CalDAV syncing structure

---

## ✅ Purpose

This repo provides the **foundational building blocks** for a complete calendar backend service, compliant with iCalendar and WebDAV/CalDAV standards.  
It is designed for developers who want to:
- Understand and implement **calendar syncing protocols**

---

## 📦 Contents

| Folder/File               | Description |
|--------------------------|-------------|
| `/pumls/`                 | PlantUML class diagrams for calendar data structure |
| `/models/`               | Django model examples conforming to RFC 5545 |
| `README.md`              | This file |
| `.env.example`           | Example config (if needed for Django project setup) |
| `LICENSE`                | MIT by default (or replace with your license)

---

## 🌐 Standards Coverage

- ✅ RFC 5545 — iCalendar: Events, Tasks, Journals, Free/Busy, Timezones
- ✅ RFC 4791 — CalDAV: Calendar syncing over WebDAV
- ✅ RFC 6350 — vCard (planned, for contact sync)
- ✅ RFC 6638 — iTIP/iMIP Scheduling (optional)
- ✅ RFC 7808 — Timezone Distribution (optional)

---

## 🧪 Current Features

- 🎯 Full PUML mapping of:
  - `VEVENT`, `VTODO`, `VTIMEZONE`, `VALARM`, `VCALENDAR`, etc.
  - Participation (RSVP, ATTENDEE roles, delegation, etc.)
  - Recurrence (`RRULE`, `RDATE`, `EXDATE`)
  - Attachments, links, reminders
  - Free/Busy support
- 🧩 Modular Django models (for drop-in use)
- 📤 Early structure for WebDAV/CalDAV endpoints

---

# Standards Overview for MVP-Compatible Calendar and Contact Sync System

This document outlines the relevant specifications and selects only the necessary components from each standard to support a **minimal viable product** for a calendar system supporting:
- **iCalendar events/tasks/freebusy/timezones** (RFC 5545)
- **CalDAV syncing and querying** (RFC 4791)
- **WebDAV storage and permissions** (RFC 4918)
- **vCard-based contact sync** (RFC 6350)
- **CardDAV sync methods** (RFC 6352)

---

## 📅 RFC 5545 - iCalendar (Core Components Required)
### Calendar Components (3.6):
- VEVENT
- VTODO
- VFREEBUSY
- VTIMEZONE
- VALARM (optional, recommended)

### Properties (3.8):
- DTSTART, DTEND, DURATION, SUMMARY, UID, SEQUENCE
- RRULE, RDATE, EXDATE, RECURRENCE-ID
- ATTENDEE, ORGANIZER, DESCRIPTION, STATUS, LOCATION
- TIMEZONE-ID, TZOFFSETFROM, TZOFFSETTO, TZNAME
- ACTION, TRIGGER, REPEAT (for VALARM)
- CREATED, LAST-MODIFIED, DTSTAMP

### Component Wrapper:
- VCALENDAR

---

## 🛋️ RFC 4791 - CalDAV
### Required for Sync and Queries:
- MKCALENDAR (5.3.1)
- calendar-query REPORT (7.8)
- calendar-multiget REPORT (7.9)
- free-busy-query (7.10)

### WebDAV Properties (5.2):
- calendar-description
- calendar-timezone
- supported-calendar-component-set
- supported-calendar-data
- max-resource-size

### Principal Discovery:
- calendar-home-set (6.2.1)
- Scheduling inbox/outbox (from RFC 6638, optionally deferred)

---

## 📂 RFC 4918 - WebDAV
### File/Calendar Resource Management:
- PROPFIND, PROPPATCH (9.1, 9.2)
- MKCOL / MKCALENDAR
- PUT, DELETE, COPY, MOVE (9.7 - 9.9)

### Locking (optional):
- LOCK, UNLOCK (9.10, 9.11)
- LOCKDISCOVERY, supported-lock properties (6.1 - 6.8)

### Required Properties:
- displayname, getetag, resourcetype, owner

---

## 🥊 RFC 6350 - vCard
### Required Properties:
- FN (Full Name)
- EMAIL
- TEL
- ADR
- UID
- KIND (individual, org, group)
- REV (last updated)

### Optional:
- PHOTO
- ORG
- TITLE
- NICKNAME
- BDAY

---

## 📡 RFC 6352 - CardDAV
### Required Sync Methods:
- addressbook-query (8.6)
- addressbook-multiget (8.7)
- REPORT (8.1)
- PUT / DELETE / PROPFIND

### Principal Property:
- addressbook-home-set

### Address Book Support:
- addressbook collection discovery (5.2)
- supported-address-data (6.2)

---

## 🚀 Minimal Class List for MVP
### iCalendar / Events:
- Calendar
- Event (VEVENT)
- Task (VTODO)
- FreeBusy (VFREEBUSY)
- Timezone (VTIMEZONE)
- Reminder (VALARM)
- Participation (ATTENDEE/ORGANIZER)

### WebDAV / CalDAV:
- WebDAVProperty
- WebDAVPermission
- WebDAVInbox / WebDAVOutbox (optional)
- WebDAVLock (optional)

### Contacts:
- Contact (vCard)
- AddressBook
- ContactGroup (optional)
- ContactSyncLog (optional)
