# Playbook

Playbook turns a goal into a step-by-step plan and finds real opportunities for
the step you're on.

You give it a resume and a goal. It researches the goal on the web, builds a
plan backwards from your deadline, and searches for programs, people, and
communities that help with the current step. When you finish something you log
it, and it decides whether you're ready for the next step.

Live at [playbook-e8xd.onrender.com](https://playbook-e8xd.onrender.com/welcome).
The [demo](https://playbook-e8xd.onrender.com/demo) needs no account.

## How it works

1. **Onboarding.** Upload a resume and answer three questions. Done once.
2. **Goal.** What you want, how you'd know you got it, the deadline, and your
   constraints.
3. **Brief.** Web research on the goal: how it works, who gets in, what it
   rewards.
4. **Plan.** Steps worked backwards from the deadline, based on what's in your
   profile.
5. **Leverage nodes.** What each step should look for: people, communities,
   programs, things to build.
6. **Scan.** A web search for the current step only. Returns real links and
   deadlines.
7. **Opportunities.** You pick the ones you'll actually do.
8. **Step review.** You log what happened. It reads that and says advance, stay,
   or not enough yet. On advance, the next step becomes current and gets its
   own scan.

The model only returns proposals. The app checks each one against a schema and
applies it when you approve, so nothing changes without you.

Built with Next.js, Supabase (auth and Postgres), and the OpenAI API.

## Run it locally

You need Node 20+ and a Supabase project. An OpenAI API key is optional.

1. Install dependencies:

   ```bash
   npm install
   ```

2. In the Supabase SQL editor, run `supabase/migrations/0001_init.sql`. It
   creates the tables and their access policies.

3. Create `.env.local` in the project root:

   ```
   PLAYBOOK_PROVIDER=openai
   OPENAI_API_KEY=sk-...
   NEXT_PUBLIC_SUPABASE_URL=https://xxxx.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=...
   ```

   No OpenAI key? Set `PLAYBOOK_PROVIDER=mock` and leave `OPENAI_API_KEY` out.
   Every stage returns canned data and the full loop still works.

4. Start it:

   ```bash
   npm run dev
   ```

   Then open <http://localhost:3000>.

To run the tests:

```bash
npm run check:all
```
