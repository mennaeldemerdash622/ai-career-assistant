# AI Career Assistant 💼

An AI-powered career assistant that helps job seekers find suitable jobs, improve their CVs, and prepare for interviews.

Users can search for jobs using natural-language requests, get detailed feedback on their CV for a specific job, generate interview questions, and write tailored cover letters. The agent selects the appropriate tools and returns clear, actionable results.

## 1. Use Case

The application is designed for students, fresh graduates, and professionals who want one assistant to support their job search instead of using separate websites and tools for searching, CV writing, and interview practice.

Users can ask questions such as:

- Find junior data analyst jobs in Cairo.
- Review my CV for this job description and tell me what to improve.
- Give me interview questions for a machine learning intern position.
- Write a cover letter for this job based on my CV.

The agent understands the request, chooses one or more tools, and combines the results into a single helpful answer. For example, it can analyze a CV against a job description and then write a matching cover letter.

## 2. LLM & Provider

**Provider:** GroqCloud
**Model:** GPT-OSS 120B
**Model ID:** `openai/gpt-oss-120b`

What they do:

- **GroqCloud:** Provides fast API access to run the language model, so no local setup is needed.
- **GPT-OSS 120B:** Understands user requests, selects tools through function calling, analyzes CVs, and writes the final answers.

Why this model: a large model is more reliable at choosing the right tool, filling in its inputs, and giving detailed, high-quality feedback on CVs and cover letters.

## 3. Agent Tools

The agent has access to four main tools.

**Tool 1: `search_jobs`**

- Description: Searches for job listings that match a job title and location.
- Input: `query` (string), `location` (string).
- Output: A list of matching jobs with title, company, location, and link.

**Tool 2: `analyze_cv`**

- Description: Compares the user's CV with a job description and identifies matching skills, missing skills, and improvements.
- Input: `cv_text` (string), `job_description` (string).
- Output: A match summary with strengths, gaps, and specific suggestions.

**Tool 3: `generate_interview_questions`**

- Description: Generates likely interview questions for a specific job role and experience level.
- Input: `job_title` (string), `level` (string).
- Output: A list of technical and behavioral interview questions.

**Tool 4: `write_cover_letter`**

- Description: Writes a tailored cover letter based on the user's CV and the job description.
- Input: `cv_text` (string), `job_description` (string).
- Output: A short, professional cover letter.

## 4. System Prompt

The system prompt defines the agent's role, available tools, and behavior.

```text
You are an AI Career Assistant. Your objective is to help job
seekers find suitable jobs, improve their CVs, and prepare for
interviews.

Available tools:
- search_jobs
- analyze_cv
- generate_interview_questions
- write_cover_letter

Instructions:
1. Understand what the user needs (job search, CV review,
   interview preparation, or cover letter) before selecting a tool.
2. Choose the most appropriate tool for the request, and use more
   than one tool when needed.
3. If the CV text, job description, job title, or location is
   missing, ask one short question first.
4. Base CV feedback only on the CV provided. Never invent
   experience, skills, degrees, or achievements.
5. When listing jobs, include title, company, location, and the
   original link when available. Never fabricate job listings.
6. Give specific and actionable feedback with concrete examples
   of improvements.
7. Keep the user's personal data private.
8. If a tool fails or information is unavailable, say so honestly.

Tone:
Be supportive, professional, honest, and concise.
Reply in the user's language.
```
