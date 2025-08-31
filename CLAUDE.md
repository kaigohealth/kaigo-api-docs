# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Mintlify documentation site for the Kaigo Platform Healthcare API. The API supports Ambi voice agents for healthcare communication scenarios including Remote Patient Monitoring (RPM), appointment reminders, follow-ups, and other patient outreach programs with strict HIPAA security compliance.

## Development Commands

### Local Development
```bash
# Install Mintlify CLI globally
npm i -g mint

# Run local development server at http://localhost:3000
mint dev

# Update to latest CLI version if dev environment isn't running
mint update
```

## Architecture & Structure

### Documentation Configuration
- **docs.json**: Main configuration file defining navigation structure, theming, and site metadata
- **api-reference/openapi.json**: Sample OpenAPI spec (Plant Store example)
- **kaigo-openapi-spec.yaml**: Main Kaigo Platform Healthcare API specification with HIPAA-compliant endpoints

### Content Organization
Documentation is organized in MDX files following this structure:
- **Root pages**: `index.mdx`, `quickstart.mdx`, `development.mdx`
- **essentials/**: Core documentation concepts (markdown, code, images, navigation, settings)
- **ai-tools/**: AI development tool integration guides
- **api-reference/**: API documentation and endpoint examples
- **snippets/**: Reusable content snippets

### API Structure
The Kaigo API implements a secure healthcare communication system with:
1. **Two-factor patient verification** before PHI access
2. **Session-based authentication** for all PHI endpoints
3. **Comprehensive audit logging** for HIPAA compliance
4. Key endpoint groups:
   - Patient verification and session management
   - Patient profile and medical information (PHI-protected)
   - Call management and scheduling
   - Escalation handling for critical situations

## Key Implementation Details

### Security Architecture
- Bearer token authentication for service-level access
- Patient session tokens required for PHI access (obtained through verification)
- Session tokens are scoped to specific calls and expire
- Phone number alone is NOT sufficient for PHI access

### API Response Patterns
- Consistent error responses with specific error codes
- Session validation on all PHI endpoints (401/403/410 responses)
- Rate limiting with headers for client awareness
- Idempotency support for critical operations

### Navigation Configuration
The site uses a two-tab structure defined in `docs.json`:
- **Guides tab**: Getting started, customization, writing content, AI tools
- **API reference tab**: API documentation and endpoint examples

## Development Workflow

When modifying the documentation:
1. Edit MDX files for content changes
2. Update `docs.json` for navigation or configuration changes
3. Modify OpenAPI specs (`.yaml` or `.json`) for API documentation updates
4. Test locally with `mint dev` before pushing changes
5. Changes to the default branch are automatically deployed via GitHub app integration

# Mintlify documentation

## Working relationship
- You can push back on ideas-this can lead to better documentation. Cite sources and explain your reasoning when you do so
- ALWAYS ask for clarification rather than making assumptions
- NEVER lie, guess, or make up information

## Project context
- Format: MDX files with YAML frontmatter
- Config: docs.json for navigation, theme, settings
- Components: Mintlify components

## Content strategy
- Document just enough for user success - not too much, not too little
- Prioritize accuracy and usability of information
- Make content evergreen when possible
- Search for existing information before adding new content. Avoid duplication unless it is done for a strategic reason
- Check existing patterns for consistency
- Start by making the smallest reasonable changes

## Frontmatter requirements for pages
- title: Clear, descriptive page title
- description: Concise summary for SEO/navigation

## Writing standards
- Second-person voice ("you")
- Prerequisites at start of procedural content
- Test all code examples before publishing
- Match style and formatting of existing pages
- Include both basic and advanced use cases
- Language tags on all code blocks
- Alt text on all images
- Relative paths for internal links

## Git workflow
- NEVER use --no-verify when committing
- Ask how to handle uncommitted changes before starting
- Create a new branch when no clear branch exists for changes
- Commit frequently throughout development
- NEVER skip or disable pre-commit hooks

## Do not
- Skip frontmatter on any MDX file
- Use absolute URLs for internal links
- Include untested code examples
- Make assumptions - always ask for clarification