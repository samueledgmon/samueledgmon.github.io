---
title: '"Evil Pong", Scream Jam 2025'
collection: portfolio
category: hackathons
excerpt: "Created the backend state machine in Unity (C#) to control game state logic, player lives, scoring, and timed chaos mix-ups for a horror-themed twist on Pong built during Scream Jam 2025.<br><br><a href='https://muddkidd.itch.io/evil-pong' target='_blank' rel='noopener noreferrer' class='btn btn--info'><i class='fas fa-fw fa-gamepad icon-pad-right' aria-hidden='true'></i>Play on itch.io</a> <a href='https://github.com/nmuddkidd/Scream-Jam-2025' target='_blank' rel='noopener noreferrer' class='btn btn--inverse'><i class='fab fa-fw fa-github icon-pad-right' aria-hidden='true'></i>View on GitHub</a>"
---

Built Evil Pong in Unity (C#) with CardGames at the University of Louisville for Scream Jam 2025. For this project, I created the backend state machine that controlled the core game state logic.

<div style="margin: 1.5em 0; padding: 1.25em 1.5em; border: 1px solid var(--global-border-color, #d0d7de); border-radius: 10px; background-color: var(--global-bg-color, #f6f8fa); display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 1em; box-shadow: 0 2px 8px rgba(0,0,0,0.06);">
  <div>
    <div style="font-size: 1.1em; margin-bottom: 0.25em;">
      <i class="fas fa-fw fa-gamepad" aria-hidden="true"></i> Evil Pong &bull; Scream Jam 2025
    </div>
    <div style="font-size: 0.9em; opacity: 0.85;">
      Unity (C#) &bull; Backend State Machine &bull; WebGL / Windows &bull; CardGames @ UofL
    </div>
  </div>
  <div style="display: flex; gap: 0.5em; flex-wrap: wrap;">
    <a href="https://muddkidd.itch.io/evil-pong" target="_blank" rel="noopener noreferrer" class="btn btn--info btn--large" style="margin-bottom: 0; white-space: nowrap;">
      <i class="fas fa-fw fa-gamepad icon-pad-right" aria-hidden="true"></i>Play on itch.io &rarr;
    </a>
    <a href="https://github.com/nmuddkidd/Scream-Jam-2025" target="_blank" rel="noopener noreferrer" class="btn btn--inverse btn--large" style="margin-bottom: 0; white-space: nowrap;">
      <i class="fab fa-fw fa-github icon-pad-right" aria-hidden="true"></i>GitHub Repo &rarr;
    </a>
  </div>
</div>

What I built and how the game works:

<ul>
  <li>Backend State Machine (State Controller): Created the central state machine that tracks and switches between game states, manages player lives and scoring mechanics, and coordinates timed gameplay events.</li>
  <li>Dynamic Ball and Chaos Mix-Ups: Connected the state controller with the ball manager so the game can trigger chaotic mix-ups on a timer, such as spawning multiple balls at once, changing ball speeds and angles, and scaling difficulty as the round goes on.</li>
  <li>Survival Gameplay Loop: Combined classic paddle-versus-AI Pong mechanics with lives-based survival and tag-based goal detection, playable directly in the browser through WebGL on itch.io.</li>
</ul>

<div style="display: flex; justify-content: center; margin: 1.5em 0;">
  <iframe frameborder="0" src="https://itch.io/embed/3965856" width="552" height="167" style="max-width: 100%; border-radius: 8px;"><a href="https://muddkidd.itch.io/evil-pong">Evil Pong by muddkidd</a></iframe>
</div>

<figure style="max-width: 480px; margin: 1.5em auto;">
  <img src="{{ '/images/EvilPong/evil_pong.png' | relative_url }}" alt="Evil Pong Cover Art">
  <figcaption>Cover artwork for Evil Pong, submitted to Scream Jam 2025 and playable in the browser on itch.io.</figcaption>
</figure>

