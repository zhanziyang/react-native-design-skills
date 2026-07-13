# React Native Design Skills

A focused collection of agent skills for designing, reviewing, and improving motion and interaction in Expo and React Native apps.

These skills translate Web-first design ideas into native interaction contracts built around platform evidence, React Native Reanimated, React Native Gesture Handler, accessibility, reduced motion, haptics, Safe Area, keyboard behavior, scroll ownership, and iOS/Android verification. They do not copy browser-only APIs into native code.

## Skills

| Skill | Use it for |
| --- | --- |
| `react-native-design-engineering` | Designing or implementing one concrete interaction, component, screen, gesture, or motion behavior |
| `review-react-native-animations` | Strict evidence-based review of a bounded interaction, file, or diff |
| `improve-react-native-animations` | Whole-project or multi-file animation audits, prioritized plans, and approved execution |
| `react-native-animation-vocabulary` | Finding the canonical name for a described mobile motion or gesture concept |
| `apple-design-react-native` | Applying fluid Apple-inspired interaction principles within Expo or React Native |
| `sync-emil-react-native-skills` | Checking Emil Kowalski's upstream skills and preparing semantic React Native ports |

## Choosing a skill

- Need the name of an effect? Start with `react-native-animation-vocabulary`.
- Need Apple-style interaction reasoning? Use `apple-design-react-native`.
- Auditing a whole app or several files? Use `improve-react-native-animations`.
- Reviewing one named interaction, file, or diff? Use `review-react-native-animations`.
- Building or polishing one concrete native interaction? Use `react-native-design-engineering`.

## Install

Clone the repository and copy the named skill folders into your Codex personal skills directory:

```bash
git clone https://github.com/zhanziyang/react-native-design-skills.git
mkdir -p ~/.codex/skills
cp -R react-native-design-skills/skills/* ~/.codex/skills/
```

Restart or reload your Codex environment after installation. You can then request a skill explicitly, for example:

```text
Use $apple-design-react-native to improve this Expo card interaction.
Use $review-react-native-animations to review this gesture implementation.
Use $sync-emil-react-native-skills to check upstream changes and report only.
```

The runtime can also select a skill automatically from its description when the request matches.

## Upstream relationship

This project is an independent React Native and Expo adaptation inspired by and derived in part from [emilkowalski/skills](https://github.com/emilkowalski/skills):

| Emil's upstream skill | React Native adaptation |
| --- | --- |
| `emil-design-eng` | `react-native-design-engineering` |
| `review-animations` | `review-react-native-animations` |
| `improve-animations` | `improve-react-native-animations` |
| `animation-vocabulary` | `react-native-animation-vocabulary` |
| `apple-design` | `apple-design-react-native` |

Updates are ported semantically: universal interaction principles may carry over, while DOM, CSS, browser, and Web-framework implementation details are replaced with evidence-based native equivalents or omitted. The `sync-emil-react-native-skills` skill records the mapping and review workflow.

This repository is unofficial and is not affiliated with or endorsed by Emil Kowalski.

## License

MIT. See [LICENSE](LICENSE). The original Emil Kowalski copyright and license notice are preserved for upstream-derived material.
