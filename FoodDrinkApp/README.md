# FoodTime Nutrition Assistant (FoodDrinkApp)

A cross-platform food and beverage nutrition tracking application developed with **.NET MAUI**, supporting both **Android** and **Windows** platforms. The application integrates mobile hardware capabilities and accessibility features, providing a complete solution for food logging, nutrition tracking, hardware interaction, and personalized display settings.


Author:Cheng Zixi 21906411


---

# Table of Contents

1. Project Overview
2. Core Features
3. Project Structure
4. Core Modules and File Descriptions
5. Environment Setup, Build and Run Guide

---

# 1. Project Overview

**FoodTime Nutrition Assistant** is a cross-platform application built with .NET MAUI. The project focuses on food and beverage management, allowing users to record foods and drinks, view nutritional information, and automatically summarize nutrition data.

The application deeply integrates native mobile device capabilities including:

* Camera access
* Geolocation services
* Text-to-Speech (TTS)
* Device vibration
* Haptic feedback

The project also follows accessibility best practices by supporting:

* Light and Dark themes
* Large font mode
* Screen reader semantic descriptions

A layered architecture separates data models, business services, and UI pages, making the project maintainable and extensible. The application connects to a MockAPI cloud service for online data storage and automatically falls back to local data when offline.

---

# 2. Core Features

## Food & Beverage Management

* Home page displaying food and beverage records using card-based layouts
* Global search functionality
* Add new food and beverage records
* Nutrition detail page
* Pull-to-refresh support for cloud synchronization

## Mobile Hardware Features

### Camera

* Capture food photos using the device camera

### Location Services

* Obtain GPS coordinates
* Reverse geocoding to retrieve country, city, and region information

### Text-to-Speech (TTS)

* Read nutrition summaries aloud
* Read application help content

### Speech Control

* Manual stop button
* Automatically stops when leaving the page

### Device Vibration

* Triggered during validation failures
* Used for nutrition reminders

### Haptic Feedback

* Dedicated testing button
* Includes usage counter for verification

## Accessibility & Personalization

### Theme Modes

* Light Mode
* Dark Mode
* Follow System Theme

### Large Font Mode

* One-click global font scaling

### Screen Reader Support

* Semantic descriptions for controls
* Accessibility labels throughout the application

### Food-Themed UI Design

* Warm color palette
* Consistent food and beverage branding

## Data Management & Error Handling

* MockAPI cloud storage
* Local fallback data when offline
* Form validation
* Exception handling for all hardware integrations
* Layered application architecture

---

# 3. Project Structure

```text
FoodDrinkApp/

├── App.xaml
├── App.xaml.cs

├── AppShell.xaml
├── AppShell.xaml.cs

├── MainPage.xaml
├── MainPage.xaml.cs

├── AddItemPage.xaml
├── AddItemPage.xaml.cs

├── FoodDetailPage.xaml
├── FoodDetailPage.xaml.cs

├── HardwarePage.xaml
├── HardwarePage.xaml.cs

├── SettingsPage.xaml
├── SettingsPage.xaml.cs

├── Directory.Build.props
├── FoodDrinkApp.csproj

├── MockAPI Configuration Guide.md
├── Project Development Guide.md

├── Models/
│   └── FoodItem.cs

├── Services/
│   ├── AccessibilityService.cs
│   ├── FoodCatalogService.cs
│   ├── MockApiConfig.cs
│   └── SpeechService.cs

├── Platforms/
│   └── Android/
│       └── AndroidManifest.xml

└── Resources/
    └── Styles/
        ├── Colors.xaml
        └── Styles.xaml
```

---

# 4. Core Modules and File Descriptions

## App.xaml / App.xaml.cs

Application startup and global resource initialization.

```csharp
return new Window(new AppShell());
```

## AppShell.xaml / AppShell.xaml.cs

Defines navigation structure and routes.

```csharp
Routing.RegisterRoute(nameof(AddItemPage), typeof(AddItemPage));
Routing.RegisterRoute(nameof(FoodDetailPage), typeof(FoodDetailPage));
```

## MainPage

Home page displaying food items, search functionality, and refresh support.

```csharp
FoodCollection.ItemsSource = FoodCatalogService.Search(query);
```

## AddItemPage

Food entry form including:

* Required field validation
* Non-negative nutrition validation
* Vibration feedback on validation failure

Validation Rules:

1. Name cannot be empty
2. Category cannot be empty
3. Description cannot be empty
4. Nutrition values must be zero or greater

## FoodDetailPage

Displays detailed nutrition information.

Features:

* Nutrition summary reading
* Speech stop button
* Vibration reminder
* Automatic speech termination

```csharp
protected override void OnDisappearing()
{
    SpeechService.Stop();
    base.OnDisappearing();
}
```

## HardwarePage

Demonstrates hardware integrations:

1. Camera
2. GPS Location
3. Reverse Geocoding
4. Text-to-Speech
5. Vibration
6. Haptic Feedback

## SettingsPage

Provides:

* Theme switching
* Accessibility settings
* Large font mode

---

# 5. Environment Setup, Build and Run Guide

## Required Environment

1. Visual Studio 2022
2. .NET MAUI Workload
3. Android SDK
4. Windows 10/11
5. Android Emulator or Physical Device

---

## Troubleshooting

### Android Startup Failure

Ensure an emulator or physical Android device is connected.

### Incorrect Location Results

Configure emulator GPS coordinates manually or use a physical device.

---

# Author

Cheng Zixi 21906411

FoodTime Nutrition Assistant (FoodDrinkApp)

Cross-Platform Food & Beverage Nutrition Tracking Application

Developed using .NET MAUI for Android and Windows platforms.
