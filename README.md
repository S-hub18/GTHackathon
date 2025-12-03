# GTHackathon
Brand Vibe: Your AI-Powered Branding Studio

Brand Vibe is a modern, AI-powered branding studio designed to help you create, manage, and scale your brand identity. The core of the application is the Brand Kit, a comprehensive profile that stores your brand's DNA—including colors, voice, values, and target audience. This kit then acts as a guiding star for AI agents, powered by Google Gemini, to generate perfectly on-brand content and visuals, from social media posts to ad creatives and marketing copy.​

✨ Key Features in Detail

🎨 Brand Kit Management

The Brand Kit is the heart of Brand Vibe. It provides a structured way to define your brand's identity, ensuring all AI-generated content is consistent and on-target. Within a Brand Kit, you can specify:​

Core Identity: Name, description, and key values.

Visuals: Primary and secondary color palettes.

Voice & Tone: Detailed descriptions of your brand's communication style (e.g., "witty and informal" or "formal and authoritative").

Products & Services: A list of your offerings with descriptions.

Target Audience: Descriptions of your ideal customer personas.

This detailed kit becomes the primary context fed to the AI for all generation tasks, including copy, posters, and ad creative variations.​

🤖 AI-Powered Content Generation

Leverage the power of Google Gemini to produce a wide range of written content tightly integrated with your Brand Kits.​

Select the Brand Kit you want to use.

Go to the "Generate" page and write a prompt for the AI (e.g., "Write a LinkedIn post announcing our new product").

The AI receives your prompt and the entire context from your selected Brand Kit, producing content that is aligned with your brand's specific voice, tone, and goals.

Generated content includes social posts, emails, website copy, and now ad captions that pair with auto-generated ad creatives.​

🖼️ AI Poster Designer

This feature provides an AI-assisted canvas to create stunning visual assets that stay on-brand. Users can start a new poster session, provide an initial description, and let an internal PosterAgent orchestrate Gemini-based analysis and image generation.​

START: The agent analyzes your description, fills in missing details (dimensions, key message, mood), and creates a session.

REPLY: It asks up to a few clarifying questions, uses smart defaults, and infers style based on your wording (e.g., "sale" → more urgent, "luxury" → more elegant).

PROMPT: The agent builds a rich, structured design prompt (brand colors, visual hierarchy, layout hints) and refines it with a text LLM.

IMAGE: A detailed prompt is sent to the image-generation backend (NanoBananaClient using Gemini 2.5 Flash Image) to produce the poster, which is stored with the session.​

REFINE: You can request changes (e.g., "make the text bigger" or "tone down the background"), and the agent adjusts the internal design representation, regenerating updated versions while keeping a version history.

📸 Auto-Creative Ad Variations (New)

Brand Vibe includes an “Auto-Creative Engine” that automatically generates multiple ad creative variations from your brand assets for fast A/B testing.​

Input: Upload or link your brand logo and a product image, and optionally provide campaign goal, platform (e.g., Meta/Instagram), target audience, tone, and mandatory copy.

Process:

The system derives a single base creative concept consistent with your Brand Kit and campaign info.

An AI agent generates 5 closely related visual prompts that represent minor, controlled variations of this base concept (e.g., subtle layout shifts, background tweaks, emphasis changes), rather than completely different designs.​

For each visual variation, the LLM also produces a matching caption variant (headline, body, CTA) that preserves the same core offer and tone with small copy tweaks for A/B testing.​

These 5 prompts are sent individually to the image-generation backend (NanoBananaClient + Gemini 2.5 Flash Image), producing 5 high-resolution ad creatives from the same core idea.​

Output:

A gallery inside the app showing the 5 ad variants with their corresponding captions side by side.

A downloadable zip file containing all 5 images plus a structured captions file (JSON/CSV) mapping each creative to its text, ready for campaigns.

The UI cleanly separates the classic “Single Poster” flow from the “Auto-Creative Ads” mode, so existing poster features remain unchanged while the new batch-creative tooling feels like a natural extension.

📈 Billboard Analyzer

The Billboard Analyzer is an innovative tool for planning and analyzing physical advertising campaigns.​

Visualize potential locations for billboard placements on an interactive map (powered by Leaflet).

Analyze the potential impact and visibility of different locations.

(Future) Integrate demographic data to better understand the audience in a specific area.

🚀 Tech Stack

Brand Vibe is built on a modern web stack designed for scalability and AI-native workflows:​

Framework: Next.js (App Router, React)

Database / Storage: Supabase (PostgreSQL) for core app data, with Prisma-style typed access patterns implied by the session and poster types.​

AI Text: Google Gemini via server-side API integration for content generation, Brand Kit–aware reasoning, and prompt engineering.

AI Image: Google Gemini 2.5 Flash Image (“Nano Banana”) accessed via an internal NanoBananaClient for poster and ad creative generation.​

Styling: Tailwind CSS

UI Components: shadcn/ui

🔧 Getting Started

Follow these instructions to get the Brand Vibe project running on your local machine.​

Prerequisites

Node.js (v20.x or higher recommended)

npm, yarn, or pnpm as your package manager

Clone the Repository

git clone https://github.com/S-hub18/brand-vibe.git

cd brand-vibe

Install Dependencies

npm install

Set Up Environment Variables

Create a file named .env.local in the root of your project and add the following variables:​

Supabase

NEXT_PUBLIC_SUPABASE_URL="your_supabase_project_url"

NEXT_PUBLIC_SUPABASE_ANON_KEY="your_supabase_anon_key"

SUPABASE_SERVICE_ROLE_KEY="your_supabase_service_role_key"

Google Gemini (Text + Image)

GOOGLE_API_KEY="your_google_ai_studio_api_key"

You can get your Supabase keys from your project's dashboard under Settings > API, and obtain your Google API key from Google AI Studio.
