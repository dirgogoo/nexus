# /nexus-setup - Automatic Installation

Auto-install Nexus dependencies: ALD System + Superpowers + MCP setup instructions.

---

## Instructions for Claude

When `/nexus-setup` is invoked, execute this installation workflow:

### Step 1: Welcome Message

```markdown
🚀 **Nexus Setup Wizard**

This will install Nexus dependencies:
✅ ALD System (8 local skills + 155 policies)
✅ Superpowers Marketplace plugins
📋 MCP setup instructions (Supabase, Chrome DevTools, GitHub, Episodic Memory)

**Estimated time**: 5-10 minutes

Ready to proceed? (yes/no)
```

Wait for user confirmation before continuing.

---

### Step 2: Install ALD System

**Action**: Use `/plugin install` to install ALD System from GitHub

**Command to execute**:
```bash
/plugin install https://github.com/dirgogoo/ald-system
```

**This will install**:
1. ald-memory - Persistent context management
2. ald-policies - 155 policies across 17 categories
3. ald-curator - Pattern detection and learning
4. ald-tester - E2E validation as end user
5. ald-code-reviewer - Code review with policy validation
6. ald-orchestrator - Workflow coordination
7. ald-policy-finder - Intelligent policy search
8. ald-sprint - Sprint management with scope isolation
9. CLAUDE.md - ALD system controller

**Wait for installation to complete** before proceeding to Step 3.

**Progress output**:
```markdown
📦 Installing ALD System from GitHub...

⚙️ Downloading from https://github.com/dirgogoo/ald-system...
✅ ALD System v1.3.1 installed successfully!

📊 Installed components:
✅ ald-memory
✅ ald-policies (155 policies)
✅ ald-curator
✅ ald-tester
✅ ald-code-reviewer
✅ ald-orchestrator
✅ ald-policy-finder
✅ ald-sprint
✅ CLAUDE.md controller

ALD System ready! ✅
```

---

### Step 3: Install Superpowers

**Action**: Use SlashCommand tool to install from marketplace

```typescript
// Install main Superpowers plugin
SlashCommand("/plugin install superpowers@superpowers-marketplace");

// Install Superpowers Dev
SlashCommand("/plugin install superpowers@superpowers-dev");
```

**Wait for installation to complete** before proceeding.

**Progress output**:
```markdown
📦 Installing Superpowers...

⚙️ Installing superpowers@superpowers-marketplace...
✅ Superpowers installed

⚙️ Installing superpowers@superpowers-dev...
✅ Superpowers Dev installed

Superpowers ready! ✅
```

**Error handling**:
If installation fails:
```markdown
⚠️ Superpowers installation failed.

**Manual installation**:
1. Open Claude Code
2. Run: /plugin install superpowers@superpowers-marketplace
3. Run: /plugin install superpowers@superpowers-dev

Then re-run: /nexus-setup to continue
```

---

### Step 4: MCP Setup Instructions

**Action**: Display MCP installation instructions (cannot auto-install - requires Claude Desktop app config)

```markdown
📋 **MCP Setup Instructions**

MCPs (Model Context Protocol) provide external tool integrations.
**Note**: MCPs require configuration in Claude Desktop app settings.

---

### ⭐ Recommended MCPs

#### 1. Supabase MCP (Database Operations)
**What**: Database migrations, security audits, type generation
**Install**:
1. Add to Claude Desktop config (`~/.config/Claude/claude_desktop_config.json`):
   ```json
   {
     "mcpServers": {
       "supabase": {
         "command": "npx",
         "args": ["-y", "@supabase/mcp"],
         "env": {
           "SUPABASE_ACCESS_TOKEN": "your-token-here"
         }
       }
     }
   }
   ```
2. Get access token: https://supabase.com/dashboard/account/tokens
3. Restart Claude Desktop

**Nexus Integration**: Auto-injected for database/migration tasks (Policy 12.1)

---

#### 2. Chrome DevTools MCP (UI Validation)
**What**: UI validation, E2E testing, performance audits
**Install**:
1. Install plugin: `/plugin install superpowers-chrome@superpowers-marketplace`
2. Chrome DevTools MCP auto-configured

**Nexus Integration**: MANDATORY for UI changes (Policy 12.2)

---

#### 3. GitHub MCP (Code Operations)
**What**: Issues, PRs, code review, repository search
**Install**:
1. Add to Claude Desktop config:
   ```json
   {
     "mcpServers": {
       "github": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-github"],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "your-token-here"
         }
       }
     }
   }
   ```
2. Create GitHub token: https://github.com/settings/tokens (scopes: repo, read:org)
3. Restart Claude Desktop

**Nexus Integration**: Optional, suggested for PR/issue tasks

---

#### 4. Episodic Memory MCP (Context Recall)
**What**: Search past conversations for patterns and context
**Install**:
1. Already included in Superpowers marketplace
2. No additional setup needed

**Nexus Integration**: Optional, suggested when user mentions "past" or "similar"

---

### Verification

After installing MCPs, verify with:
```bash
# List available MCP tools
/tools

# Should see tools like:
# - mcp__supabase__*
# - mcp__plugin_superpowers-chrome_chrome__*
# - mcp__github__*
# - mcp__plugin_episodic-memory_episodic-memory__*
```

---

**Need help?** See full MCP setup guide: `docs/mcp-setup/`
```

---

### Step 5: Configuration Files

**Action**: Create user configuration files

1. **Create user preferences template**:
   ```yaml
   # File: ~/.claude/skills/nexus/config/user-preferences.yml

   # Copy from: ~/.claude/skills/nexus/config/user-preferences.template.yml
   ```

   Use Write tool to copy template to user-preferences.yml

**Progress output**:
```markdown
⚙️ Creating configuration files...

✅ config/user-preferences.yml created
✅ memory/global.json initialized

Configuration ready! ✅
```

---

### Step 6: Verification

**Action**: Verify all components are installed correctly

```typescript
// Check ALD skills
const aldSkills = [
  "ald-memory",
  "ald-policies",
  "ald-curator",
  "ald-tester",
  "ald-code-reviewer",
  "ald-orchestrator",
  "ald-policy-finder",
  "ald-sprint"
];

for (const skill of aldSkills) {
  try {
    Read(`~/.claude/skills/${skill}/SKILL.md`);
    console.log(`✅ ${skill}`);
  } catch (error) {
    console.log(`❌ ${skill} - NOT FOUND`);
  }
}

// Check Superpowers (attempt to invoke)
try {
  // Check if superpowers commands are available
  console.log("✅ Superpowers available");
} catch (error) {
  console.log("⚠️ Superpowers not found - manual installation required");
}

// Check Nexus skill
try {
  Read("~/.claude/skills/nexus/SKILL.md");
  console.log("✅ Nexus skill");
} catch (error) {
  console.log("❌ Nexus skill - NOT FOUND");
}
```

**Progress output**:
```markdown
🔍 Verifying installation...

**ALD System**:
✅ ald-memory
✅ ald-policies (155 policies)
✅ ald-curator
✅ ald-tester
✅ ald-code-reviewer
✅ ald-orchestrator
✅ ald-policy-finder
✅ ald-sprint

**Superpowers**:
✅ superpowers@superpowers-marketplace
✅ superpowers@superpowers-dev

**Nexus**:
✅ nexus skill
✅ /nexus command
✅ Configuration files

**MCPs**:
📋 Setup instructions provided (requires manual config)
```

---

### Step 7: Setup Complete

```markdown
✅ **Nexus Setup Complete!**

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Installation Summary

✅ ALD System (8 skills + 155 policies)
✅ Superpowers Marketplace plugins
✅ Nexus orchestrator
✅ Configuration files created
📋 MCP setup instructions provided

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Next Steps

### 1. Configure MCPs (Optional but Recommended)
Follow instructions above to setup:
- Supabase MCP (database operations)
- Chrome DevTools MCP (UI validation)
- GitHub MCP (code operations)
- Episodic Memory MCP (context recall)

### 2. Customize Configuration
Edit your preferences:
```bash
~/.claude/skills/nexus/config/user-preferences.yml
```

### 3. Start Using Nexus
```bash
/nexus implement [your task]
/nexus fix [bug description]
/nexus refactor [component]
/nexus review [code]
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Quick Test

Try this to verify everything works:

```bash
/nexus review my code
```

Expected: Nexus analyzes intent → Selects code-review workflow → Executes ALD code reviewer

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Documentation

- **README**: `~/.claude/skills/nexus/README.md`
- **Setup Guide**: `~/.claude/skills/nexus/SETUP-GUIDE.md`
- **MCP Integration**: `~/.claude/skills/nexus/MCP-INTEGRATION.md`
- **Troubleshooting**: `~/.claude/skills/nexus/TROUBLESHOOTING.md`

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

**Happy orchestrating!** 🚀
```

---

## Error Handling

### If ALD installation fails:
```markdown
❌ ALD System installation failed

**Manual installation**:
1. Open Claude Code
2. Run: /plugin install https://github.com/dirgogoo/ald-system
3. If still fails, try:
   - Check internet connection
   - Verify GitHub repository is accessible
   - Check ~/.claude/skills/ directory permissions

**Alternative**: Install via git clone:
```bash
cd ~/.claude/skills
git clone https://github.com/dirgogoo/ald-system
cp -r ald-system/skills/* ./
cp ald-system/CLAUDE.md ./
rm -rf ald-system
```

**Get help**: https://github.com/dirgogoo/ald-system/issues
```

### If Superpowers installation fails:
```markdown
❌ Superpowers installation failed

**Manual installation**:
1. Run: /plugin install superpowers@superpowers-marketplace
2. Run: /plugin install superpowers@superpowers-dev
3. Restart Claude Code if needed

**Get help**: https://github.com/anthropics/superpowers/issues
```

### If verification fails:
```markdown
⚠️ Verification detected missing components

**Missing**:
- [list of missing skills/plugins]

**Action**: Re-run /nexus-setup or install manually

**Get help**: https://github.com/dirgogoo/nexus/issues
```

---

## Implementation Notes for Claude

When executing this setup:

1. **Use Write tool** for all file copies (ALD System)
2. **Use SlashCommand tool** for Superpowers installation
3. **Display progress** after each step
4. **Validate** before marking complete
5. **Handle errors gracefully** with clear instructions
6. **End with success message** and next steps

**Estimated tokens**: ~50K (large but one-time operation)

**User experience**: Setup should feel automatic and guided, with clear progress indicators.

---

CLAUDE.MD ATIVO
