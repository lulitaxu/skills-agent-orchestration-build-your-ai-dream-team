# Project Pulse Dashboard Implementation Plan

## Goal

Build a static Project Pulse dashboard that presents project names, owners, statuses, recent activity, priorities, and contributor summaries in a clear, responsive, accessible interface.

## Responsibilities

### Planner

- Define the dashboard architecture and page structure.
- Define the project data shape and required fields.
- Establish accessibility requirements and validation criteria.
- Document edge cases and the expected behavior for each.

### Designer

- Own information hierarchy and responsive layout guidance.
- Define visual styling, including status badges and project-card treatment.
- Ensure sufficient color contrast and accessible states.
- Provide guidance for keyboard navigation, focus visibility, and narrow viewports.

### Coder

- Implement semantic HTML in `app/index.html`, including stylesheet and data references and `.project-card` elements.
- Implement the responsive layout and visual styling in `app/styles.css`.
- Create `app/project-data.json` with valid top-level `projects` JSON containing `name`, `owner`, `status`, `recentActivity`, and `priority` for each project.
- Create `.vscode/launch.json` with a strict launch configuration named `Run Project Pulse Dashboard` that serves `${workspaceFolder}/app` via `python3 -m http.server 5500` and opens `http://localhost:%s/index.html`.

## Dependencies

- The data schema must be defined before rendering is implemented.
- Designer guidance must be available before final CSS and markup decisions.
- HTML implementation depends on the CSS and JSON structure and references.
- The launch configuration depends on the completed app directory structure.

## Parallel Work Decisions

- Run Designer guidance and Coder data/launch preparation in parallel after the Planner establishes the architecture, schema, accessibility requirements, and validation expectations.
- Follow with integrated implementation once the design guidance and data/launch preparation are available.
- Do not finalize markup or CSS independently of the agreed data shape and design guidance.

## Sequential Phases

1. **Planner:** Define architecture, data shape, accessibility requirements, validation expectations, and edge-case behavior.
2. **Designer/Coder kickoff:** Designer defines hierarchy, responsive layout, visual styling, status badges, card treatment, contrast, and accessibility guidance; Coder prepares the data file and launch configuration in parallel.
3. **Integration:** Coder implements the semantic HTML, stylesheet, project data rendering, references, and project cards using the Planner and Designer outputs.
4. **Launch and browser validation:** Start the configured server, verify the browser-facing dashboard, and confirm that `index.html` opens at the expected URL.
5. **Review:** Validate the integrated result against the requirements, accessibility expectations, responsive behavior, and edge cases.

## Validation Expectations

- Parse `app/project-data.json` as JSON and verify that it has a top-level `projects` array.
- Verify that project records provide the required `name`, `owner`, `status`, `recentActivity`, and `priority` fields.
- Verify that `app/index.html` references the stylesheet and JSON data correctly and contains or renders `.project-card` elements.
- Verify selectors, required fields, and references used by the dashboard.
- Verify status and priority presentation, including badges and card treatment.
- Verify `.vscode/launch.json` is valid and includes the `Run Project Pulse Dashboard` configuration, `python3 -m http.server 5500`, `${workspaceFolder}/app`, and the URL pattern `http://localhost:%s/index.html`.
- Open `index.html` through the configured browser/server flow rather than relying only on a file-system view.
- Check responsive behavior at narrow viewport widths.
- Check accessibility, including semantic structure, color contrast, visible focus states, keyboard navigation, and understandable status/priority labels.
- Check edge cases:
  - An empty `projects` array displays a useful empty state.
  - Missing fields do not break rendering and are represented safely.
  - Unknown status or priority values receive a safe fallback presentation.
  - A failed JSON load displays a useful error state.
  - A narrow viewport remains readable and usable without unintended horizontal overflow.
  - Keyboard navigation reaches all interactive elements in a logical order.
  - A port conflict is reported or handled without silently presenting a misleading success state.
