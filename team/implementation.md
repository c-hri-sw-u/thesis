# Thesis AI Team - Implementation Guide

## Status
✅ **Step 1 Complete:** AI Team Prompts Created
- PM (Project Manager)
- Research Lead
- Technical Lead
- HCI Researcher
- Devil's Advocate
- Note-taker

✅ **Step 2 Complete:** Skill Configuration Created
- Command routing structure defined
- Subagent mappings defined
- Utility commands designed

🚧 **Step 3 Pending:** Create Subagents
- Need to use `sessions_spawn` to create 6 subagents
- Each subagent will load its corresponding prompt file

⏳ **Step 4 Pending:** OpenClaw Integration
- Install skill in OpenClaw
- Test command routing
- Verify Discord integration

---

## Team Members

| Role | Command | Label | Prompt File |
|------|---------|--------|-------------|
| Project Manager | `/pm` | `thesis-pm` | `team/prompts/pm.txt` |
| Research Lead | `/research` | `thesis-research` | `team/prompts/research.txt` |
| Technical Lead | `/tech` | `thesis-tech` | `team/prompts/tech.txt` |
| HCI Researcher | `/hci` | `thesis-hci` | `team/prompts/hci.txt` |
| Devil's Advocate | `/da` | `thesis-da` | `team/prompts/da.txt` |
| Note-taker | `/notes` | `thesis-notes` | `team/prompts/notes.txt` |

---

## Commands

### Core Team Commands
```
/pm [query]          → Project Manager
/research [query]      → Research Lead
/tech [query]         → Technical Lead
/hci [query]          → HCI Researcher
/da [query]           → Devil's Advocate
/notes [action]       → Note-taker
```

### Utility Commands
```
/standup              → Daily standup (all members)
/status               → Overall thesis progress
/team                 → List team members
/help                 → Command reference
```

---

## Implementation Steps

### Step 3: Create Subagents

```bash
# Create 6 AI team members
sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/pm.txt)" \
  --label "thesis-pm" \
  --model "zai/glm-4.7"

sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/research.txt)" \
  --label "thesis-research" \
  --model "zai/glm-4.7"

sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/tech.txt)" \
  --label "thesis-tech" \
  --model "zai/glm-4.7"

sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/hci.txt)" \
  --label "thesis-hci" \
  --model "zai/glm-4.7"

sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/da.txt)" \
  --label "thesis-da" \
  --model "zai/glm-4.7"

sessions_spawn \
  --task "$(cat /Users/mia/.openclaw/workspace/thesis/team/prompts/notes.txt)" \
  --label "thesis-notes" \
  --model "zai/glm-4.7"
```

### Step 4: Test Commands

```discord
# Test basic routing
/pm status
/research find multimodal memory
/tech design memory system
/hci study design
/da critique our approach
/notes summarize

# Test utility commands
/standup
/status
/team
/help
```

---

## Command Handler Logic

```python
# Pseudo-code for OpenClaw integration
class ThesisCommandsHandler:
    def __init__(self):
        self.subagents = {
            'pm': 'thesis-pm',
            'research': 'thesis-research',
            'tech': 'thesis-tech',
            'hci': 'thesis-hci',
            'da': 'thesis-da',
            'notes': 'thesis-notes'
        }
        
        self.utility_commands = {
            'standup': self.run_daily_standup,
            'status': self.show_status,
            'team': self.show_team,
            'help': self.show_help
        }
    
    async def handle(self, command, args):
        # Utility commands
        if command in self.utility_commands:
            return await self.utility_commands[command](args)
        
        # Route to subagent
        subagent_key = self.subagents.get(command)
        if subagent_key:
            query = ' '.join(args)
            response = await sessions_send(
                sessionKey=subagent_key,
                message=query
            )
            role = command.upper()
            return f"**{role}:**\n\n{response}"
        
        return f"❌ Unknown command: /{command}\n\nUse /help for available commands"
    
    async def run_daily_standup(self, args):
        # Query all team members
        members = ['thesis-pm', 'thesis-research', 'thesis-tech', 'thesis-hci', 'thesis-da']
        agenda = "## Daily Standup\n\n### Progress"
        
        for member in members:
            response = await sessions_send(
                sessionKey=member,
                message="Daily standup: progress, updates, blockers"
            )
            agenda += f"\n\n### {member}\n{response}"
        
        # Get summary from note-taker
        summary = await sessions_send(
            sessionKey='thesis-notes',
            message=f"Summarize this meeting:\n\n{agenda}"
        )
        
        return f"📊 **Daily Standup**\n\n{summary}"
    
    async def show_status(self, args):
        # Read progress files and calculate percentages
        progress = await self.calculate_progress()
        
        return f"""📈 **Thesis Status** - Week {progress['week']} of 20

### Overall Progress
- Phase 1 (Lit Review): {progress['phase1']}% ✅
- Phase 2 (System Design): {progress['phase2']}% 🚧
- Phase 3 (Implementation): {progress['phase3']}% ⏳
- Phase 4 (Evaluation): {progress['phase4']}% ⏳
- Phase 5 (Writing): {progress['phase5']}% ⏳

### Next Deadline
📅 {progress['next_deadline']['title']}: {progress['next_deadline']['date']}
   - {progress['next_deadline']['days']} days remaining

### Recent Activity
{progress['recent_activity']}
"""
    
    async def show_team(self, args):
        return """👥 **Thesis AI Team**

### Core Members
1. **Project Manager** (`/pm`)
   - 🎯 Focus: Timeline, progress, deadlines
   - 💬 Style: Organized, practical, deadline-oriented
   - ⏱️ Typical response: 10-30 seconds

2. **Research Lead** (`/research`)
   - 📚 Focus: Papers, literature review, research gaps
   - 💬 Style: Academic, thorough, critical
   - ⏱️ Typical response: 30-60 seconds

3. **Technical Lead** (`/tech`)
   - 🛠️ Focus: System design, implementation, feasibility
   - 💬 Style: Technical, pragmatic, solution-oriented
   - ⏱️ Typical response: 20-45 seconds

4. **HCI Researcher** (`/hci`)
   - 👥 Focus: User study, privacy, ethics, user perceptions
   - 💬 Style: Empathetic, user-centric, ethical
   - ⏱️ Typical response: 25-50 seconds

5. **Devil's Advocate** (`/da`)
   - 🤔 Focus: Critique, alternatives, risks, challenges
   - 💬 Style: Critical, skeptical, constructive
   - ⏱️ Typical response: 20-40 seconds

6. **Note-taker** (`/notes`)
   - 📝 Focus: Summarize, extract actions, track decisions
   - 💬 Style: Concise, structured, action-oriented
   - ⏱️ Typical response: 5-15 seconds

### Utility
- `/standup` - Daily standup with all members
- `/status` - Overall progress
- `/help` - Command reference
"""
    
    async def show_help(self, args):
        return """🤖 **Thesis AI Team Commands**

### Core Team Commands
`/pm [query]` - Project Manager (timeline, progress, deadlines)
`/research [query]` - Research Lead (papers, literature review, gaps)
`/tech [query]` - Technical Lead (system design, implementation)
`/hci [query]` - HCI Researcher (user study, privacy, ethics)
`/da [query]` - Devil's Advocate (critique, alternatives, risks)
`/notes [action]` - Note-taker (summarize, extract actions, track decisions)

### Utility Commands
`/standup` - Trigger daily standup (all team members)
`/status` - Show overall thesis progress
`/team` - List all team members and roles
`/help` - Show this command reference

### Examples
`/pm status` - Check overall progress
`/research find multimodal memory` - Find papers
`/tech design memory system` - Design component
`/hci study design personalization` - Design user study
`/da critique our approach` - Get critical feedback
`/notes summarize` - Summarize recent messages

### Tips
- Use `/team` to see all roles
- Commands route to specialized subagents
- DA will challenge assumptions - expect pushback!
- `/notes summarize` after meetings to capture decisions
"""
```

---

## Next Actions

### Immediate (This Week)
1. ✅ **Completed:** Create prompt files for all 6 team members
2. ✅ **Completed:** Create skill configuration
3. 🚧 **TODO:** Create 6 subagents using `sessions_spawn`
4. 🚧 **TODO:** Install skill in OpenClaw
5. 🚧 **TODO:** Test basic commands in Discord
6. 🚧 **TODO:** Debug and refine based on testing

### This Week Goals
- All 6 subagents created and running
- Basic command routing working
- `/pm`, `/research`, `/tech` commands functional
- `/standup`, `/status`, `/team` commands functional

### Next Week Goals
- Refine prompts based on actual interactions
- Implement `/notes` advanced features (extract, decisions, log)
- Test `standup` automation
- Optimize response formatting

---

## File Structure

```
thesis/
├── team/
│   ├── prompts/
│   │   ├── pm.txt          ✅ Created
│   │   ├── research.txt    ✅ Created
│   │   ├── tech.txt        ✅ Created
│   │   ├── hci.txt         ✅ Created
│   │   ├── da.txt          ✅ Created
│   │   └── notes.txt       ✅ Created
│   ├── skill.json            ✅ Created
│   └── implementation.md    ✅ Created (this file)
```

---

*Last updated: 2026-02-27*
*Status: Ready to create subagents*
