# HireFlow AI

An agentic hiring pipeline for a single organisation: job seekers apply to Jobs, and each Application is screened and assessed by AI before a Recruiter shortlists them for a Live Interview.

## People

**Candidate**:
A person who applies to Jobs, identified by their email address, phone number and name. Candidates have no account; one Candidate may apply to many Jobs.
_Avoid_: Applicant, customer, user, job seeker (in code)

**Recruiter**:
A staff member of the organisation who creates Jobs, approves their questions, sets Rubrics and Pass Thresholds, and makes Final Decisions. The only kind of user with an account.
_Avoid_: Admin, hiring manager, reviewer

## Pipeline

**Job**:
A position at the organisation, described by a job description, a Rubric, Pass Thresholds and approved questions. A Job is Open or Closed; closing it stops new Applications only.
_Avoid_: Role, posting, vacancy, JD (as an entity name)

**Job Version**:
A frozen snapshot of a Job's Rubric, Pass Thresholds, weights and questions. Editing a Job creates a new Job Version; each Application stays bound to the one current when it applied.
_Avoid_: Revision, job snapshot

**Application**:
One Candidate applying to one Job, with the CV they uploaded for it; the unit the pipeline runs on. A Candidate has at most one Application per Job.
_Avoid_: Submission, candidacy

**Duplicate Application**:
A new Application for a Job that already has one with the same email, or with the same phone number and name. It is refused and the existing Application's status is shown instead.
_Avoid_: Re-application, repeat

**Stage**:
One AI-run step an Application passes through, in order: Screening, then Assessment. Falling below a Stage's Pass Threshold rejects the Application.
_Avoid_: Step, phase, round

**Screening**:
The Stage that scores how well an Application's CV matches the Job.
_Avoid_: CV matching, CV parsing, CV checking

**Assessment**:
The Stage after Screening: a single proctored online session made of the Written Test followed by the Voice Interview, passed or failed on its combined score.
_Avoid_: Online test, exam

**Written Test**:
The first half of the Assessment, where the Candidate types answers to the Job's approved theoretical questions, each under its own timer.
_Avoid_: Test, quiz, questionnaire

**Voice Interview**:
The second half of the Assessment, where an AI interviewer asks the Job's approved questions aloud, with no follow-ups, and the Candidate answers each by speaking under its own timer.
_Avoid_: Verbal test, voice test, audio test, call

**Pass Threshold**:
The minimum score an Application must reach to pass a Stage, set by the Recruiter per Job: a match percentage for Screening, and a combined score out of 100 for the Assessment.
_Avoid_: Cutoff, passing mark, threshold %

**Needs Review**:
The state of an Application the AI could not score after a retry (e.g. a missing transcript or a score without Evidence). It waits for a Recruiter and is never rejected by the system's own failure.
_Avoid_: Error, failed, stuck

**Shortlisting**:
A Recruiter's review of an Application that has passed every Stage, approving it for a Live Interview or rejecting it. The first point at which a human acts on an Application.
_Avoid_: Approval, review, human gate

**Booking Link**:
A link, emailed to a shortlisted Candidate, to a page where they pick a Live Interview slot from the interviewer's availability.
_Avoid_: Calendly link, scheduling link, invite

**Live Interview**:
A video interview between a shortlisted Candidate and a senior technical person, held outside HireFlow.
_Avoid_: Next round, technical round, meeting

**Final Decision**:
A Recruiter's record, after the Live Interview, of whether the Candidate is Hired or Rejected. It closes the Application.
_Avoid_: Outcome, verdict

## Scoring

**Rubric**:
The list of Criteria a Job is assessed against, shared by every Stage.
_Avoid_: Scorecard, requirements

**Criterion**:
One named, weighted, scorable quality in a Rubric, scored in the Stages it is assigned to (e.g. "Python depth", "English Fluency", "Delivery"). Voice Interview Criteria are scored only from what the transcript shows, never from tone or accent.
_Avoid_: Skill, dimension, competency

**Evidence**:
A cited span from the CV, a Written Test answer or a Voice Interview transcript that justifies a score on a Criterion. A score without Evidence is invalid.
_Avoid_: Justification, reasoning

**Assessment Score**:
The combined score out of 100 for an Assessment: the Written Test and Voice Interview scores, weighted as the Recruiter sets per Job.
_Avoid_: Total marks, final score

## Assessment

**Assessment Link**:
The one signed link, emailed to the Candidate after passing Screening, that gives access to the Assessment for one Application. The Assessment must be started within 48 hours of the link being issued.
_Avoid_: Test link, interview link, invite, token

**Integrity Signal**:
A recorded proctoring observation during the Assessment: a browser event (focus loss, copy or paste, fullscreen exit) or a webcam observation (no face, a second person).
_Avoid_: Cheating flag, violation

**Warning**:
An Integrity Signal counted against the Candidate and shown to them. One count covers the whole Assessment; exceeding 5 Warnings rejects the Application with the reason recorded.
_Avoid_: Strike, violation

**Reinstatement**:
A Recruiter overriding an AI rejection so the Application continues to its next step. The Candidate is emailed that their application is continuing.
_Avoid_: Override, appeal, un-reject
