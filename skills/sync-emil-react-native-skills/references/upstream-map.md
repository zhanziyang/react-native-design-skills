# Upstream Mapping

## Source-to-target ownership

| Upstream path | Installed skill name | Porting focus |
| --- | --- | --- |
| `skills/emil-design-eng/SKILL.md` | `react-native-design-engineering` | Direct design and implementation principles |
| `skills/review-animations/SKILL.md` | `review-react-native-animations` | Strict review rules and output contract |
| `skills/improve-animations/SKILL.md` | `improve-react-native-animations` | Whole-project audit and improvement planning |
| `skills/animation-vocabulary/SKILL.md` | `react-native-animation-vocabulary` | Platform-neutral terminology and native mappings |
| `skills/apple-design/SKILL.md` | `apple-design-react-native` | Apple-inspired interaction principles translated to Expo/RN |
| `skills/find-animation-opportunities/SKILL.md` | `find-react-native-animation-opportunities` | Read-only discovery of high-value missing native motion |

Resolve installed directories by frontmatter name at runtime. Do not persist installation directory IDs here.

## Classification

| Classification | Meaning | Default action |
| --- | --- | --- |
| Universal principle | Platform-independent judgment, interaction model, vocabulary, or review criterion | Port the intent into the mapped target |
| Web implementation | CSS, DOM, browser API, Web library, mouse/hover, or Web performance advice | Translate the behavior; reject literal API copying |
| New capability | New upstream section, workflow, skill, or materially expanded responsibility | Evaluate target ownership and ask before structural changes |
| Irrelevant change | README wording, installation instructions, images, typo-only edits, or unrelated metadata | No local content edit; checkpoint may advance after approval |

## Cross-cutting invariants

Every port must retain:

- Expo/React Native iOS and Android scope.
- Hard stops for Web-only and SwiftUI/UIKit/Compose/Views implementation.
- Inspection of installed dependency versions before naming APIs.
- Direct manipulation, interruption, velocity, cancellation, and gesture ownership where relevant.
- Reduced Motion, non-gesture alternatives, restrained haptics, and platform-specific verification.
- Separation of observed, code-supported, and unverified claims.
- Deterministic routing among the six mapped installed skills.

When an upstream change affects more than one mapped skill, report and validate each target separately.
