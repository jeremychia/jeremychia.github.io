---
layout: default
title: Working With Me
nav: true
nav_order: 5
footer: true
description: A working manual for teammates and collaborators.
---

{% assign wm = site.data[site.active_lang]['work-with-me'] %}
{% if wm == nil %}{% assign wm = site.data['en']['work-with-me'] %}{% endif %}

<style>
  .wm-card {
    background: white;
    border-radius: 0.75rem;
    border: 1px solid #f3f4f6;
    padding: 1.5rem;
    transition: box-shadow 0.2s;
  }
  .wm-card:hover { box-shadow: 0 4px 12px rgba(0,0,0,0.08); }

  .wm-accent-blue  { border-left: 4px solid #60a5fa; }
  .wm-accent-red   { border-left: 4px solid #f87171; }
  .wm-accent-green { border-left: 4px solid #4ade80; }
  .wm-accent-dark  { border-left: 4px solid #1e293b; }

  .wm-bg-green  { background: #f0fdf4; border: 1px solid #bbf7d0; border-radius: 1rem; padding: 1.5rem; }
  .wm-bg-red    { background: #fef2f2; border: 1px solid #fecaca; border-radius: 1rem; padding: 1.5rem; }
  .wm-bg-amber  { background: #fffbeb; border: 1px solid #fde68a; border-radius: 1rem; padding: 1.5rem; }
  .wm-bg-neutral{ background: #f9fafb; border-radius: 1rem; padding: 1.5rem; }

  .wm-pill {
    display: inline-block;
    background: #1e293b;
    color: white;
    border-radius: 9999px;
    padding: 0.375rem 0.875rem;
    font-size: 0.875rem;
    font-weight: 500;
    margin: 0.25rem;
  }
  .wm-chip {
    display: inline-block;
    background: #f1f5f9;
    color: #475569;
    border-radius: 9999px;
    padding: 0.25rem 0.75rem;
    font-size: 0.8125rem;
    font-weight: 500;
    margin: 0.25rem;
  }

  .wm-tabs { border-bottom: 1px solid #e5e7eb; margin-bottom: 2rem; display: flex; overflow-x: auto; }
  .wm-tab {
    padding: 0.75rem 1.25rem;
    font-size: 0.875rem;
    font-weight: 500;
    white-space: nowrap;
    border-bottom: 2px solid transparent;
    color: #6b7280;
    cursor: pointer;
    background: none;
    border-top: none;
    border-left: none;
    border-right: none;
    transition: color 0.15s;
  }
  .wm-tab:hover { color: #111827; }
  .wm-tab.active { border-bottom-color: #111827; color: #111827; font-weight: 600; }

  .wm-compat-track { flex: 1; height: 8px; background: #e5e7eb; border-radius: 9999px; overflow: hidden; }
  .wm-compat-fill  { height: 100%; border-radius: 9999px; background: #22c55e; transition: width 0.3s; width: 0%; }

  .wm-badge {
    flex-shrink: 0;
    width: 1.5rem;
    height: 1.5rem;
    background: #1e293b;
    color: white;
    border-radius: 9999px;
    font-size: 0.75rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .wm-section-title {
    font-size: 1.125rem;
    font-weight: 600;
    border-left: 4px solid #1e293b;
    padding-left: 0.75rem;
    margin-bottom: 1rem;
  }
  .wm-impression-box { text-align: center; padding: 1rem; background: #f9fafb; border-radius: 0.5rem; }
  .wm-reality-box    { text-align: center; padding: 1rem; background: #eff6ff; border: 1px solid #bfdbfe; border-radius: 0.5rem; }

  .wm-dot { display: inline-block; width: 0.375rem; height: 0.375rem; border-radius: 9999px; margin-top: 0.375rem; flex-shrink: 0; }
  .wm-dot-green { background: #22c55e; }
  .wm-dot-red   { background: #ef4444; }

  /* Dark mode */
  .dark .wm-card         { background: #1e293b; border-color: #334155; }
  .dark .wm-bg-neutral   { background: #334155; }
  .dark .wm-bg-green     { background: rgba(20,83,45,0.2); border-color: rgba(21,128,61,0.3); }
  .dark .wm-bg-red       { background: rgba(127,29,29,0.2); border-color: rgba(185,28,28,0.3); }
  .dark .wm-bg-amber     { background: rgba(120,53,15,0.2); border-color: rgba(180,83,9,0.4); color: #fde68a; }
  .dark .wm-bg-amber *   { color: #fde68a !important; }
  .dark .wm-pill         { background: white; color: #1e293b; }
  .dark .wm-chip         { background: #334155; color: #94a3b8; }
  .dark .wm-tabs         { border-bottom-color: #334155; }
  .dark .wm-tab:hover    { color: white; }
  .dark .wm-tab.active   { border-bottom-color: white; color: white; }
  .dark .wm-compat-track { background: #334155; }
  .dark .wm-badge        { background: white; color: #1e293b; }
  .dark .wm-section-title { border-left-color: white; }
  .dark .wm-accent-dark  { border-left-color: white; }
  .dark .wm-impression-box { background: #334155; }
  .dark .wm-reality-box  { background: rgba(30,58,138,0.2); border-color: rgba(59,130,246,0.3); }
</style>

<section class="container mx-auto px-4 py-16" style="max-width: 52rem;">

  <!-- Hero / Manifesto -->
  <div class="text-center" style="margin-bottom: 3rem;">
    <blockquote style="font-size: 2rem; font-weight: 700; line-height: 1.3; margin-bottom: 1rem;">
      "{{ wm.manifesto.quote }}"
    </blockquote>
    <p class="text-gray-600" style="font-size: 1.125rem; margin-bottom: 1.5rem;">
      {{ wm.manifesto.subtitle }}
    </p>
    <div>
      {% for chip in wm.manifesto.chips %}
      <span class="wm-chip">{{ chip }}</span>
      {% endfor %}
      <span class="wm-chip" style="background: #eff6ff; color: #1d4ed8;">Blue / Red dominant</span>
    </div>
  </div>

  <!-- Personality at a glance -->
  <div class="wm-bg-neutral" style="margin-bottom: 3rem;">
    <p style="font-size: 0.75rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.05em; color: #6b7280; margin-bottom: 1rem;">
      {{ wm.personality.section_label }}
    </p>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      {% for trait in wm.personality.traits %}
      <div style="border-left: 3px solid {{ trait.color }}; padding-left: 0.75rem;">
        <div style="font-weight: 600; color: {{ trait.text_color }}; font-size: 0.875rem; margin-bottom: 0.25rem;">{{ trait.label }}</div>
        <div class="text-sm text-gray-600">{{ trait.description }}</div>
      </div>
      {% endfor %}
    </div>
    <p class="text-sm text-gray-500" style="margin-top: 1rem;">{{ wm.personality.attribution }}</p>
  </div>

  <!-- Tabs -->
  <div>
    <div class="wm-tabs" role="tablist">
      <button class="wm-tab active" data-tab="how-i-work"      role="tab" aria-selected="true">{{ wm.tabs.how_i_work }}</button>
      <button class="wm-tab"        data-tab="values"          role="tab" aria-selected="false">{{ wm.tabs.values }}</button>
      <button class="wm-tab"        data-tab="energisers"      role="tab" aria-selected="false">{{ wm.tabs.energisers }}</button>
      <button class="wm-tab"        data-tab="working-with-me" role="tab" aria-selected="false">{{ wm.tabs.working_with_me }}</button>
    </div>

    <!-- Tab: How I Work -->
    <div id="tab-how-i-work" role="tabpanel">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

        {% for card in wm.how_i_work.cards %}
        {% assign accent_color = "#3b82f6" %}
        {% assign icon_path = "M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" %}
        {% if card.accent == "red" %}{% assign accent_color = "#ef4444" %}{% assign icon_path = "M13 10V3L4 14h7v7l9-11h-7z" %}{% endif %}
        {% if card.accent == "green" %}{% assign accent_color = "#22c55e" %}{% assign icon_path = "M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" %}{% endif %}
        {% if card.accent == "blue" and forloop.index == 3 %}{% assign icon_path = "M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" %}{% endif %}

        <div class="wm-card wm-accent-{{ card.accent }}">
          <div style="display: flex; align-items: center; gap: 0.75rem; margin-bottom: 1rem;">
            <svg style="width: 1.25rem; height: 1.25rem; color: {{ accent_color }}; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="{{ icon_path }}"/>
            </svg>
            <h3 style="font-weight: 600;">{{ card.title }}</h3>
          </div>
          <ul class="text-sm text-gray-600" style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
            {% for point in card.points %}<li>{{ point }}</li>{% endfor %}
          </ul>
          <div style="margin-top: 1rem; padding-top: 1rem; border-top: 1px solid #f3f4f6;">
            <button class="wm-tab-link text-sm" style="color: #3b82f6; cursor: pointer; background: none; border: none; padding: 0;" data-target="{{ card.link_tab }}">{{ card.link_label }}</button>
          </div>
        </div>
        {% endfor %}

        <div class="wm-card wm-accent-red" style="grid-column: 1 / -1;">
          <div style="display: flex; align-items: center; gap: 0.75rem; margin-bottom: 1rem;">
            <svg style="width: 1.25rem; height: 1.25rem; color: #ef4444; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"/>
            </svg>
            <h3 style="font-weight: 600;">{{ wm.how_i_work.leader.title }}</h3>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <ul class="text-sm text-gray-600" style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.how_i_work.leader.col1 %}<li>{{ item }}</li>{% endfor %}
            </ul>
            <ul class="text-sm text-gray-600" style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.how_i_work.leader.col2 %}<li>{{ item }}</li>{% endfor %}
            </ul>
          </div>
          <div style="margin-top: 1rem; padding-top: 1rem; border-top: 1px solid #f3f4f6;">
            <button class="wm-tab-link text-sm" style="color: #3b82f6; cursor: pointer; background: none; border: none; padding: 0;" data-target="{{ wm.how_i_work.leader.link_tab }}">{{ wm.how_i_work.leader.link_label }}</button>
          </div>
        </div>

      </div>
    </div>

    <!-- Tab: Values -->
    <div id="tab-values" style="display: none;" role="tabpanel">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6" style="margin-bottom: 2rem;">

        <div>
          <h3 class="wm-section-title">{{ wm.values.non_negotiables_title }}</h3>
          <div>
            {% for pill in wm.values.pills %}<span class="wm-pill">{{ pill }}</span>{% endfor %}
          </div>
          <p class="text-sm text-gray-500" style="margin-top: 1rem;">{{ wm.values.non_negotiables_note }}</p>
        </div>

        <div style="display: flex; flex-direction: column; gap: 1.5rem;">
          <div>
            <h3 style="font-size: 1.125rem; font-weight: 600; color: #16a34a; margin-bottom: 0.75rem;">{{ wm.values.green_flags_title }}</h3>
            <ul style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.values.green_flags %}
              <li style="display: flex; align-items: flex-start; gap: 0.5rem;" class="text-sm text-gray-700"><span style="color: #22c55e; flex-shrink: 0; margin-top: 0.1rem;">✓</span>{{ item }}</li>
              {% endfor %}
            </ul>
          </div>
          <div>
            <h3 style="font-size: 1.125rem; font-weight: 600; color: #dc2626; margin-bottom: 0.75rem;">{{ wm.values.red_flags_title }}</h3>
            <ul style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.values.red_flags %}
              <li style="display: flex; align-items: flex-start; gap: 0.5rem;" class="text-sm text-gray-700"><span style="color: #ef4444; flex-shrink: 0; margin-top: 0.1rem;">✗</span>{{ item }}</li>
              {% endfor %}
            </ul>
          </div>
        </div>

      </div>

      <!-- Compatibility checker -->
      <div class="wm-bg-neutral">
        <h3 style="font-weight: 600; margin-bottom: 0.5rem;">{{ wm.values.compat_title }}</h3>
        <p class="text-sm text-gray-500" style="margin-bottom: 1.25rem;">{{ wm.values.compat_subtitle }}</p>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4" style="margin-bottom: 1.25rem;">
          {% for item in wm.values.compat_items %}
          <label style="display: flex; align-items: flex-start; gap: 0.75rem; cursor: pointer;">
            <input type="checkbox" class="flag-check" style="width: 1rem; height: 1rem; margin-top: 0.2rem; flex-shrink: 0; accent-color: #22c55e;">
            <span class="text-sm text-gray-700">{{ item }}</span>
          </label>
          {% endfor %}
        </div>
        <div style="display: flex; align-items: center; gap: 0.75rem;">
          <div class="wm-compat-track"><div class="wm-compat-fill" id="compat-bar"></div></div>
          <span class="text-sm" style="font-weight: 500;" id="compat-score">0 / {{ wm.values.compat_items | size }} match</span>
        </div>
        <p class="text-sm text-gray-500" id="compat-label" style="margin-top: 0.5rem;">{{ wm.values.compat_labels[0] }}</p>
      </div>
    </div>

    <!-- Tab: Energisers -->
    <div id="tab-energisers" style="display: none;" role="tabpanel">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

        <div class="wm-bg-green">
          <div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 1.25rem;">
            <svg style="width: 1.25rem; height: 1.25rem; color: #16a34a; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
            </svg>
            <h3 style="font-weight: 600; color: #166534;">{{ wm.energisers.energises_title }}</h3>
          </div>
          <ul style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.75rem;">
            {% for item in wm.energisers.energises %}
            <li style="display: flex; align-items: flex-start; gap: 0.5rem;" class="text-sm"><span class="wm-dot wm-dot-green"></span>{{ item }}</li>
            {% endfor %}
          </ul>
        </div>

        <div class="wm-bg-red">
          <div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 1.25rem;">
            <svg style="width: 1.25rem; height: 1.25rem; color: #dc2626; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18.364 18.364A9 9 0 005.636 5.636m12.728 12.728A9 9 0 015.636 5.636m12.728 12.728L5.636 5.636"/>
            </svg>
            <h3 style="font-weight: 600; color: #991b1b;">{{ wm.energisers.drains_title }}</h3>
          </div>
          <ul style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.75rem;">
            {% for item in wm.energisers.drains %}
            <li style="display: flex; align-items: flex-start; gap: 0.5rem;" class="text-sm"><span class="wm-dot wm-dot-red"></span>{{ item }}</li>
            {% endfor %}
          </ul>
        </div>

      </div>

      <div class="wm-card wm-accent-dark" style="margin-top: 1.5rem;">
        <h3 class="wm-section-title">{{ wm.energisers.optimising_title }}</h3>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          {% for item in wm.energisers.optimising %}
          <div style="display: flex; align-items: flex-start; gap: 0.75rem;">
            <span class="wm-badge">{{ forloop.index }}</span>
            <div>
              <div style="font-weight: 500; font-size: 0.875rem;">{{ item.title }}</div>
              <div class="text-sm text-gray-500">{{ item.subtitle }}</div>
            </div>
          </div>
          {% endfor %}
        </div>
      </div>
    </div>

    <!-- Tab: Working With Me -->
    <div id="tab-working-with-me" style="display: none;" role="tabpanel">
      <div style="display: flex; flex-direction: column; gap: 1.5rem;">

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="wm-card wm-accent-blue">
            <h3 style="font-weight: 600; margin-bottom: 1rem;">{{ wm.working_with_me.feedback_give_title }}</h3>
            <ul class="text-sm text-gray-600" style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.working_with_me.feedback_give %}<li>{{ item }}</li>{% endfor %}
            </ul>
          </div>
          <div class="wm-card wm-accent-red">
            <h3 style="font-weight: 600; margin-bottom: 1rem;">{{ wm.working_with_me.feedback_how_title }}</h3>
            <ul class="text-sm text-gray-600" style="list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.5rem;">
              {% for item in wm.working_with_me.feedback_how %}<li>{{ item }}</li>{% endfor %}
            </ul>
          </div>
        </div>

        <div class="wm-card">
          <h3 class="wm-section-title">{{ wm.working_with_me.manage_title }}</h3>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            {% for item in wm.working_with_me.manage %}
            <div style="display: flex; align-items: flex-start; gap: 0.75rem;" class="text-sm text-gray-600"><span style="color: #22c55e; flex-shrink: 0; margin-top: 0.1rem;">✓</span>{{ item }}</div>
            {% endfor %}
          </div>
        </div>

        <div class="wm-card">
          <h3 class="wm-section-title">{{ wm.working_with_me.impression_title }}</h3>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-4" style="align-items: center;">
            <div class="wm-impression-box">
              <div class="text-sm" style="font-weight: 500; color: #6b7280; margin-bottom: 0.5rem;">{{ wm.working_with_me.impression_label }}</div>
              <div class="text-sm">{{ wm.working_with_me.impression_text }}</div>
            </div>
            <div style="display: flex; justify-content: center; align-items: center; padding: 1rem 0;">
              <svg style="width: 1.5rem; height: 1.5rem; color: #9ca3af;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
              </svg>
            </div>
            <div class="wm-reality-box">
              <div class="text-sm" style="font-weight: 500; color: #1d4ed8; margin-bottom: 0.5rem;">{{ wm.working_with_me.reality_label }}</div>
              <div class="text-sm">{{ wm.working_with_me.reality_text }}</div>
            </div>
          </div>
          <p class="text-sm text-gray-500" style="text-align: center; margin-top: 1rem;">{{ wm.working_with_me.impression_note }}</p>
        </div>

        <div class="wm-bg-amber">
          <div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 1rem;">
            <svg style="width: 1.25rem; height: 1.25rem; color: #d97706; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/>
            </svg>
            <h3 style="font-weight: 600; color: #92400e;">{{ wm.working_with_me.pitfalls_title }}</h3>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            {% for pitfall in wm.working_with_me.pitfalls %}
            <div class="text-sm" style="color: #78350f;"><strong>{{ pitfall.strong }}</strong> {{ pitfall.text }}</div>
            {% endfor %}
          </div>
        </div>

      </div>
    </div>

  </div>

  <!-- About You -->
  <div style="margin-top: 3rem; padding-top: 3rem; border-top: 1px solid #e5e7eb;">
    <div style="display: flex; align-items: center; gap: 0.75rem; margin-bottom: 0.75rem;">
      <svg style="width: 1.25rem; height: 1.25rem; color: #6b7280; flex-shrink: 0;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/>
      </svg>
      <h2 style="font-size: 1.25rem; font-weight: 700;">{{ wm.about_you.title }}</h2>
    </div>
    <p class="text-gray-500" style="font-size: 0.9375rem; margin-bottom: 1.75rem; max-width: 40rem;">{{ wm.about_you.subtitle }}</p>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      {% for q in wm.about_you.questions %}
      <div class="wm-card" style="display: flex; flex-direction: column; gap: 0.75rem;">
        <p class="text-sm text-gray-700" style="margin: 0; font-weight: 500;">{{ q.question }}</p>
        <div style="border-top: 1px solid #e5e7eb; padding-top: 0.75rem; display: flex; flex-direction: column; gap: 0.375rem;">
          <p class="text-sm text-gray-500" style="margin: 0; font-style: italic;">{{ q.why }}</p>
          <button class="wm-tab-link text-sm" style="color: #3b82f6; cursor: pointer; background: none; border: none; padding: 0; text-align: left;" data-target="{{ q.link_tab }}">{{ q.link_label }}</button>
        </div>
      </div>
      {% endfor %}
    </div>
  </div>

</section>

<script>
(function() {
  var tabs = document.querySelectorAll('.wm-tab');
  var panelIds = ['tab-how-i-work', 'tab-values', 'tab-energisers', 'tab-working-with-me'];

  function activateTab(targetId) {
    tabs.forEach(function(btn) {
      var isActive = btn.dataset.tab === targetId;
      btn.classList.toggle('active', isActive);
      btn.setAttribute('aria-selected', isActive ? 'true' : 'false');
    });
    panelIds.forEach(function(id) {
      var el = document.getElementById(id);
      if (el) el.style.display = (id === 'tab-' + targetId) ? '' : 'none';
    });
  }

  tabs.forEach(function(btn) {
    btn.addEventListener('click', function() { activateTab(btn.dataset.tab); });
  });

  document.querySelectorAll('.wm-tab-link').forEach(function(link) {
    link.addEventListener('click', function() {
      activateTab(link.dataset.target);
      var targetBtn = document.querySelector('.wm-tab[data-tab="' + link.dataset.target + '"]');
      if (targetBtn) targetBtn.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
    });
  });

  var checks = document.querySelectorAll('.flag-check');
  var bar = document.getElementById('compat-bar');
  var scoreEl = document.getElementById('compat-score');
  var labelEl = document.getElementById('compat-label');
  var total = checks.length;
  var labels = [{% for l in wm.values.compat_labels %}'{{ l | escape }}'{% unless forloop.last %},{% endunless %}{% endfor %}];

  function updateChecker() {
    var checked = document.querySelectorAll('.flag-check:checked').length;
    var pct = Math.round((checked / total) * 100);
    if (bar) bar.style.width = pct + '%';
    if (scoreEl) scoreEl.textContent = checked + ' / ' + total + ' match';
    if (labelEl && labels[checked]) labelEl.textContent = labels[checked];
  }

  checks.forEach(function(cb) { cb.addEventListener('change', updateChecker); });
})();
</script>
