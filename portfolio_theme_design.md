# Passion-Infused Interactive Portfolio Theme

This document provides the complete technical design breakdown, Tailwind CSS configuration, component architecture, and raw React code snippets for Gowtham Selvaraj's personal developer portfolio theme.

---

## 1. Theme & Color Palette Concept

| Passion / Layer | Accent Name | Hex / Tailored Class | Creative Mapping |
| :--- | :--- | :--- | :--- |
| **Movies & Cinema (Base)** | Obsidian Charcoal | `#0D0E12` (`bg-cinematic-bg`) | Dark atmospheric background with film-grain textures & radial spotlight overlays |
| **Cooking (Secondary Accent)** | Saffron Amber / Spiced Terracotta | `#F59E0B` / `#EA580C` | Highlights technical "recipes", ingredients, badges, and primary action buttons |
| **Travelling (Exploration)** | Sky Blue / Cyan | `#38BDF8` / `#06B6D4` | Flight itinerary passport layout, destination pins, and map widgets |
| **Music (Dynamic Pulses)** | Neon Violet / Electric Magenta | `#A855F7` / `#EC4899` | Interactive equalizer audio visualizer, spinning vinyl album art, and glow borders |
| **Friends & Community** | Warm Amber / Gold | `#FBBF24` | Soft polaroid card frames, team hackathon moments, and warm lighting |

---

## 2. Tailwind CSS Configuration (`tailwind.config.js`)

Add the following color and animation extensions to your `tailwind.config.js`:

```javascript
module.exports = {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        cinematic: {
          bg: '#0D0E12',
          surface: '#14161C',
          card: '#181A20',
          border: '#2A2D36',
          polaroid: '#1E2028'
        },
        cooking: {
          saffron: '#F59E0B',
          terracotta: '#EA580C',
          amber: '#D97706'
        },
        travel: {
          sky: '#38BDF8',
          cyan: '#06B6D4',
          sunset: '#F43F5E'
        },
        music: {
          violet: '#A855F7',
          magenta: '#EC4899',
          neon: '#C084FC'
        },
        friends: {
          gold: '#FBBF24',
          warm: '#FEF08A'
        }
      },
      animation: {
        'equalizer': 'equalizer 1.2s ease-in-out infinite alternate',
        'spin-slow': 'spin 12s linear infinite',
        'pulse-glow': 'pulseGlow 3s ease-in-out infinite',
      },
      keyframes: {
        equalizer: {
          '0%': { height: '15%' },
          '50%': { height: '100%' },
          '100%': { height: '35%' }
        },
        pulseGlow: {
          '0%, 100%': { opacity: '0.4' },
          '50%': { opacity: '0.8' }
        }
      }
    }
  }
}
```

---

## 3. Component Architecture Breakdown

- `App` (Root State Container)
  - `Navbar` (Fixed Glassmorphic Header)
  - `HeroSection` (Living Dashboard with Dynamic Floating Passion Toggles)
  - `BentoGridPassions` ("Life Outside Code" - Music Player, Polaroid Gallery, Travel Map, Culinary Pantry)
  - `AboutSection` (Professional Full-Stack Overview)
  - `SkillsIngredients` (Categorized Skills Badges)
  - `ExperienceItinerary` (Flight Itinerary Passport Log)
  - `ProjectsRecipeCards` (Movie Poster Cards with Technical Recipe Breakdown)
  - `EducationCredentials` (Academic Passport & Certificates)
  - `ContactCinemaTicket` (Dual-Stub Retro Cinema Access Pass)
  - `Footer` (Copyright & Theme Credits)

---

## 4. Hero Section React Code Snippet (Living Dashboard)

```jsx
import React, { useState } from 'react';

export const LivingHeroSection = () => {
    const [activePassion, setActivePassion] = useState('all');

    const passions = [
        { id: 'movies', name: 'Movies', icon: 'fa-film', color: 'border-red-500 text-red-400 bg-red-950/40' },
        { id: 'cooking', name: 'Cooking', icon: 'fa-utensils', color: 'border-amber-500 text-amber-400 bg-amber-950/40' },
        { id: 'travel', name: 'Travelling', icon: 'fa-plane-departure', color: 'border-sky-500 text-sky-400 bg-sky-950/40' },
        { id: 'music', name: 'Music', icon: 'fa-music', color: 'border-purple-500 text-purple-400 bg-purple-950/40' },
        { id: 'friends', name: 'Friends', icon: 'fa-user-group', color: 'border-yellow-500 text-yellow-400 bg-yellow-950/40' }
    ];

    return (
        <section className="relative pt-36 pb-24 px-6 bg-[#0D0E12]">
            {/* Filter Vibe Badges */}
            <div className="mb-10 flex flex-wrap gap-3">
                <button 
                    onClick={() => setActivePassion('all')}
                    className={`px-3.5 py-1.5 rounded-full text-xs font-semibold ${activePassion === 'all' ? 'bg-slate-100 text-slate-900' : 'bg-[#181A20] text-slate-400'}`}
                >
                    ✨ All Passions
                </button>
                {passions.map(p => (
                    <button
                        key={p.id}
                        onClick={() => setActivePassion(p.id)}
                        className={`px-3.5 py-1.5 rounded-full text-xs font-semibold flex items-center gap-2 border ${activePassion === p.id ? p.color : 'bg-[#181A20] text-slate-400 border-[#2A2D36]'}`}
                    >
                        <i className={`fas ${p.icon}`}></i>
                        <span>{p.name}</span>
                    </button>
                ))}
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
                <div className="lg:col-span-5 flex justify-center">
                    <div className="relative max-w-sm w-full">
                        <div className="bg-[#181A20] p-3 rounded-3xl border border-[#2A2D36] shadow-2xl">
                            <img src="profile.png" alt="Gowtham Selvaraj" className="w-full rounded-2xl" />
                        </div>
                    </div>
                </div>
                <div className="lg:col-span-7">
                    <h1 className="text-5xl font-extrabold text-slate-100 mb-4">Gowtham Selvaraj</h1>
                    <h2 className="text-3xl font-bold text-amber-500 mb-6">MERN Stack & Full Stack Developer</h2>
                    <p className="text-slate-300 text-lg mb-6">Building high-performance web applications across MongoDB, Express.js, React, Node.js, Python, FastAPI, Django, and PostgreSQL.</p>
                </div>
            </div>
        </section>
    );
};
```

---

## 5. "Life Outside Code" Bento Grid React Code Snippet

```jsx
import React, { useState } from 'react';

export const BentoGridPassions = () => {
    const [isPlayingMusic, setIsPlayingMusic] = useState(true);

    return (
        <section className="py-24 px-6 bg-[#14161C]">
            <div className="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-12 gap-6">
                {/* Music Player Widget */}
                <div className="md:col-span-6 bg-[#181A20] p-6 rounded-2xl border border-[#2A2D36]">
                    <div className="flex justify-between items-center mb-4">
                        <h3 className="text-slate-200 font-bold text-sm">Coding Rhythm Playlist</h3>
                        <span className="text-xs font-mono text-purple-400">Live Vibe</span>
                    </div>
                    <div className="flex items-center gap-4">
                        <div className={`w-16 h-16 rounded-full bg-slate-950 border-4 border-slate-800 flex items-center justify-center ${isPlayingMusic ? 'animate-spin' : ''}`}>
                            <div className="w-4 h-4 rounded-full bg-purple-500"></div>
                        </div>
                        <div>
                            <p className="font-bold text-slate-100">Midnight Code & Coffee</p>
                            <p className="text-xs text-slate-400">Lofi Focus Beats</p>
                        </div>
                    </div>
                </div>

                {/* Polaroid Frame */}
                <div className="md:col-span-6 bg-[#181A20] p-6 rounded-2xl border border-[#2A2D36]">
                    <h3 className="text-slate-200 font-bold text-sm mb-4">Friends & Team Moments</h3>
                    <div className="bg-[#1E2028] p-3 rounded-xl border border-[#2A2D36]">
                        <p className="text-xs text-center font-semibold text-slate-300">Sprint Planning & Pair Programming</p>
                    </div>
                </div>
            </div>
        </section>
    );
};
```
