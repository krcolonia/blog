---
title: Revisiting Code Quest
date: 2025-11-17 02:17:00 +800
categories:
  - Programming
  - Game Development
tags:
  - Code-Quest
---

## A little bit of context
Code Quest was my Capstone project for my 3rd and 4th year of college, and was developed for just around less than a year. It was developed using Godot 4.3, used Firebase for its cloud-saving functionalities, and used CodeX by Jaagrav for the code compilation, but has since then temporarily used jDoodle due to CodeX's API endpoint being down.

It originally started off as just an average game-based learning app that presents itself as a game, but no actual gameplay, just incentivized learning on a roadmap. It was even supposed to have its own sort of scripting language called CQScript (which, to be honest, was dumb of me to think of).

Over time however, it evolved into having actual RPG gameplay elements, a quasi-open world, and cloud saving features implemented using Firebase (this is an important topic later on). This is what Code Quest is currently.

After finishing our final defense for the project, my work on the game itself came to a halt, since working on it nonstop for months on end took a toll on my motivation to work on the game.

But then, just recently, I suddenly had the urge to update my portfolio site and came across an archived version of my repository for Code Quest, which made me want to work on it again and possibly even maintain it properly.

## Revisiting the game
After I went and cloned the last version I'd work on back on my laptop, I went ahead and set the project up to run on my laptop.

Seeing the original boot screen for the game was a mix of nostalgia, and possibly PTSD from the coffee-induced sleepless nights I worked on making even that part of the game work.

After running the game and making sure everything worked well, I figured that I'd want to take a look into the code and, as I've expected, it was a glorious mess.

However the most important thing I want to talk about here is Firebase (see, told you it'd be a topic here!). Because I ran the game to test if it still works, I went ahead and made a new project instance. Lo and behold, I found out that Firebase Storage now requires a billing plan!

The main reason I opted for Firebase was that it was accessible, and storage was free! Now that it wasn't I had to look for alternatives and instead opted for Supabase.

Although the two are BaaS, the main difference is that Supabase is actually running on FOSS such as PostgreSQL, and their free tier plan was enough for my use case.

## Migrating from Firebase to Supabase
I thought that migrating from Firebase to Supabase was gonna be easy. I mean, Firebase runs on NoSQL for their RDB and Supabase runs Postgres, but I structured my Firebase RDB to be like a relational db. It shouldn't that be hard **right**?

Well, that's where I went wrong. Although both services provide a way to connect via REST APIs (which is the backbone of Code Quest), the way they implement things was very different.

I tried using a community-made plugin that connects your Supabase project to Godot, but setup was unnecessarily complicated for me. So I did what any sensible human being would do.

I just programmed my own implementation. By basing off of the code made by fenix for the Supabase addon.

As of this date, the only implementation I've had running where the Sign Up and Sign In functions, but it was definitely a step in the right direction. Supabase had actually opened up my game's authentication features to more providers compared to Firebase.

I'll be sharing more updates through this blog about Code Quest, since I find working on it at my own pace is much more relaxing than working on it to meet a school deadline. That's all for now!