{
  "name": "AI Job Application Auto-Filler + Brand Content Automation",
  "nodes": [
    {
      "parameters": {},
      "id": "manual-trigger",
      "name": "Manual Job Search Trigger",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [240, 300]
    },
    {
      "parameters": {
        "rule": {
          "interval": [
            {
              "field": "hours",
              "hoursInterval": 6
            }
          ]
        }
      },
      "id": "schedule-trigger",
      "name": "Auto-Run Every 6 Hours",
      "type": "n8n-nodes-base.scheduleTrigger",
      "typeVersion": 1.2,
      "position": [240, 420]
    },
    {
      "parameters": {
        "content": "=## 📋 YOUR RESUME DATA\n\n**Name:** [Your Full Name]\n**Email:** your-email@gmail.com\n**Phone:** (555) 123-4567\n**Location:** [Your City, State]\n**LinkedIn:** linkedin.com/in/yourprofile\n**Portfolio:** yourfishingbrand.com\n\n**PROFESSIONAL SUMMARY:**\nEntrepreneurial e-commerce professional with proven social media marketing expertise and advanced technical automation skills. Successfully built and operate Shopify-based fishing tackle brand with substantial social media following. Expert in Docker containerization, API integration, and workflow automation (n8n). Combines creative content creation with technical implementation for business growth.\n\n**TECHNICAL SKILLS:**\n- E-commerce: Shopify, Drop Shipping Operations\n- DevOps: Docker, Docker Compose, Linux (Bookworm OS)\n- Automation: n8n workflows, MCP servers, API integration\n- Hardware: Raspberry Pi 5, Hailo AI acceleration\n- APIs: Google Gemini, DeepSeek, RESTful services\n- Content: Video editing, social media management\n- Systems: Wyoming Whisper server, Piper TTS\n\n**EXPERIENCE:**\n\n**Founder & Operator** | Fishing Tackle E-commerce Brand | [Date] - Present\n- Built profitable Shopify drop shipping business from ground up\n- Grew substantial social media following through original fishing content\n- Manage entire digital marketing, inventory, and customer service operations\n- Created and edited 100+ pieces of engaging fishing video content\n\n**Technical Infrastructure Developer** | Personal Projects | [Date] - Present\n- Designed and deployed Docker-based MCP server infrastructure\n- Implemented AI-powered automation workflows using n8n\n- Configured Raspberry Pi 5 with Hailo AI acceleration for edge computing\n- Integrated multiple API services (Gemini, DeepSeek) for intelligent automation\n- Built Wyoming Whisper speech recognition and Piper TTS server stack\n\n**EDUCATION:**\n[Your Education]\n\n**AVAILABILITY:** Immediate",
        "height": 737.547619047619,
        "width": 459.5238095238095
      },
      "id": "resume-data",
      "name": "📋 YOUR RESUME INFO (EDIT THIS)",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [700, 300]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "full_name",
              "name": "full_name",
              "value": "Your Full Name",
              "type": "string"
            },
            {
              "id": "email",
              "name": "email",
              "value": "your.email@gmail.com",
              "type": "string"
            },
            {
              "id": "phone",
              "name": "phone",
              "value": "(555) 123-4567",
              "type": "string"
            },
            {
              "id": "location",
              "name": "location",
              "value": "Your City, State",
              "type": "string"
            },
            {
              "id": "linkedin",
              "name": "linkedin",
              "value": "linkedin.com/in/yourprofile",
              "type": "string"
            },
            {
              "id": "portfolio",
              "name": "portfolio",
              "value": "yourfishingbrand.com",
              "type": "string"
            },
            {
              "id": "years_experience",
              "name": "years_experience",
              "value": "3",
              "type": "string"
            },
            {
              "id": "resume_summary",
              "name": "resume_summary",
              "value": "Entrepreneurial e-commerce professional with proven social media marketing expertise and advanced technical automation skills. Successfully built and operate Shopify-based fishing tackle brand with substantial social media following. Expert in Docker containerization, API integration, and workflow automation. Combines creative content creation with technical implementation for business growth.",
              "type": "string"
            },
            {
              "id": "technical_skills",
              "name": "technical_skills",
              "value": "Shopify, Drop Shipping, Docker, Docker Compose, Linux, n8n, MCP servers, API Integration, Raspberry Pi, Hailo AI, Google Gemini, DeepSeek, Video Editing, Social Media Marketing, Content Creation, Wyoming Whisper, Piper TTS, REST APIs",
              "type": "string"
            },
            {
              "id": "work_experience",
              "name": "work_experience",
              "value": "[{\"title\": \"Founder & Operator\", \"company\": \"Fishing Tackle E-commerce Brand\", \"dates\": \"2023 - Present\", \"achievements\": [\"Built profitable Shopify drop shipping business\", \"Grew substantial social media following through original content\", \"Manage digital marketing and operations\", \"Created 100+ fishing video content pieces\"]}, {\"title\": \"Technical Infrastructure Developer\", \"company\": \"Personal Projects\", \"dates\": \"2023 - Present\", \"achievements\": [\"Designed Docker-based MCP server infrastructure\", \"Implemented AI-powered n8n automation workflows\", \"Configured Raspberry Pi 5 with Hailo AI acceleration\", \"Integrated Google Gemini and DeepSeek APIs\", \"Built Wyoming Whisper and Piper TTS server stack\"]}]",
              "type": "string"
            },
            {
              "id": "education",
              "name": "education",
              "value": "Your Education Here",
              "type": "string"
            },
            {
              "id": "cover_letter_style",
              "name": "cover_letter_style",
              "value": "professional, enthusiastic, results-focused, showcasing both creative and technical abilities",
              "type": "string"
            },
            {
              "id": "availability",
              "name": "availability",
              "value": "Immediate - Can start within 1 week",
              "type": "string"
            },
            {
              "id": "salary_expectation",
              "name": "salary_expectation",
              "value": "Flexible based on role and responsibilities",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "set-resume",
      "name": "Load Resume Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [460, 300]
    },
    {
      "parameters": {
        "url": "https://remotive.com/api/remote-jobs",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "search",
              "value": "ecommerce social media devops docker shopify marketing"
            },
            {
              "name": "limit",
              "value": "100"
            }
          ]
        },
        "options": {}
      },
      "id": "job-search-api",
      "name": "Search Remote Jobs (Remotive)",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [680, 500]
    },
    {
      "parameters": {
        "operation": "split",
        "fieldToSplitOut": "jobs",
        "options": {}
      },
      "id": "split-jobs",
      "name": "Split Job Results",
      "type": "n8n-nodes-base.itemLists",
      "typeVersion": 3.3,
      "position": [900, 500]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "job_title",
              "name": "job_title",
              "value": "={{ $json.title }}",
              "type": "string"
            },
            {
              "id": "company",
              "name": "company",
              "value": "={{ $json.company_name }}",
              "type": "string"
            },
            {
              "id": "location",
              "name": "location",
              "value": "={{ $json.candidate_required_location || 'Remote' }}",
              "type": "string"
            },
            {
              "id": "job_url",
              "name": "job_url",
              "value": "={{ $json.url }}",
              "type": "string"
            },
            {
              "id": "description",
              "name": "description",
              "value": "={{ $json.description }}",
              "type": "string"
            },
            {
              "id": "salary",
              "name": "salary",
              "value": "={{ $json.salary || 'Not specified' }}",
              "type": "string"
            },
            {
              "id": "category",
              "name": "category",
              "value": "={{ $json.category }}",
              "type": "string"
            },
            {
              "id": "tags",
              "name": "tags",
              "value": "={{ $json.tags ? $json.tags.join(', ') : '' }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "normalize-job",
      "name": "Normalize Job Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [1120, 500]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent",
        "authentication": "predefinedCredentialType",
        "nodeCredentialType": "googleGeminiOAuth2Api",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"contents\": [{\n    \"parts\": [{\n      \"text\": \"You are an expert job application assistant. Analyze this job posting and determine if it's a good match for the candidate.\\n\\n**CANDIDATE PROFILE:**\\nName: {{ $('Load Resume Data').item.json.full_name }}\\nSummary: {{ $('Load Resume Data').item.json.resume_summary }}\\nSkills: {{ $('Load Resume Data').item.json.technical_skills }}\\nExperience: {{ $('Load Resume Data').item.json.work_experience }}\\n\\n**JOB POSTING:**\\nTitle: {{ $json.job_title }}\\nCompany: {{ $json.company }}\\nLocation: {{ $json.location }}\\nDescription: {{ $json.description.substring(0, 2000) }}\\n\\nProvide a JSON response with:\\n{\\n  \\\"match_score\\\": <0-100>,\\n  \\\"key_matches\\\": [\\\"skill/experience that matches\\\"],\\n  \\\"concerns\\\": [\\\"any gaps or mismatches\\\"],\\n  \\\"recommendation\\\": \\\"APPLY_NOW\\\" or \\\"REVIEW\\\" or \\\"SKIP\\\",\\n  \\\"reasoning\\\": \\\"brief explanation\\\"\\n}\"\n    }]\n  }],\n  \"generationConfig\": {\n    \"temperature\": 0.3,\n    \"topK\": 40,\n    \"topP\": 0.95,\n    \"maxOutputTokens\": 1024\n  }\n}",
        "options": {}
      },
      "id": "analyze-match",
      "name": "AI: Analyze Job Match",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [1340, 500],
      "credentials": {
        "googleGeminiOAuth2Api": {
          "id": "YOUR_CREDENTIAL_ID",
          "name": "Google Gemini API"
        }
      }
    },
    {
      "parameters": {
        "jsCode": "// Parse the Gemini response\nconst response = JSON.parse($input.item.json.body);\nconst aiText = response.candidates[0].content.parts[0].text;\n\n// Extract JSON from potential markdown code blocks\nlet jsonText = aiText;\nif (aiText.includes('```json')) {\n  jsonText = aiText.split('```json')[1].split('```')[0].trim();\n} else if (aiText.includes('```')) {\n  jsonText = aiText.split('```')[1].split('```')[0].trim();\n}\n\nconst analysis = JSON.parse(jsonText);\n\n// Combine with job data\nreturn {\n  json: {\n    ...($('Normalize Job Data').item.json),\n    ...analysis\n  }\n};"
      },
      "id": "parse-ai-response",
      "name": "Parse AI Analysis",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [1560, 500]
    },
    {
      "parameters": {
        "conditions": {
          "options": {
            "caseSensitive": true,
            "leftValue": "",
            "typeValidation": "strict"
          },
          "conditions": [
            {
              "id": "score-check",
              "leftValue": "={{ $json.match_score }}",
              "rightValue": "65",
              "operator": {
                "type": "number",
                "operation": "gte"
              }
            }
          ],
          "combinator": "and"
        },
        "options": {}
      },
      "id": "filter-matches",
      "name": "Filter Good Matches (65+)",
      "type": "n8n-nodes-base.filter",
      "typeVersion": 2,
      "position": [1780, 500]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent",
        "authentication": "predefinedCredentialType",
        "nodeCredentialType": "googleGeminiOAuth2Api",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"contents\": [{\n    \"parts\": [{\n      \"text\": \"Generate a tailored cover letter for this job application.\\n\\n**CANDIDATE INFO:**\\nName: {{ $('Load Resume Data').item.json.full_name }}\\nEmail: {{ $('Load Resume Data').item.json.email }}\\nPhone: {{ $('Load Resume Data').item.json.phone }}\\nSummary: {{ $('Load Resume Data').item.json.resume_summary }}\\nSkills: {{ $('Load Resume Data').item.json.technical_skills }}\\nExperience: {{ $('Load Resume Data').item.json.work_experience }}\\n\\n**JOB DETAILS:**\\nPosition: {{ $json.job_title }}\\nCompany: {{ $json.company }}\\nDescription: {{ $json.description.substring(0, 1500) }}\\n\\n**STYLE:** {{ $('Load Resume Data').item.json.cover_letter_style }}\\n\\nWrite a compelling, personalized cover letter that:\\n1. Opens with enthusiasm for the specific role\\n2. Highlights 2-3 most relevant experiences from candidate background\\n3. Connects candidate's unique blend of e-commerce AND technical skills\\n4. Shows understanding of company/role requirements\\n5. Closes with strong call to action\\n6. Keep it under 400 words\\n7. Professional but personable tone\\n\\nFormat as a complete cover letter ready to paste into application.\"\n    }]\n  }],\n  \"generationConfig\": {\n    \"temperature\": 0.7,\n    \"maxOutputTokens\": 2048\n  }\n}",
        "options": {}
      },
      "id": "generate-cover-letter",
      "name": "AI: Generate Custom Cover Letter",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [2000, 500],
      "credentials": {
        "googleGeminiOAuth2Api": {
          "id": "YOUR_CREDENTIAL_ID",
          "name": "Google Gemini API"
        }
      }
    },
    {
      "parameters": {
        "jsCode": "// Parse cover letter from Gemini response\nconst response = JSON.parse($input.item.json.body);\nconst coverLetter = response.candidates[0].content.parts[0].text;\n\nreturn {\n  json: {\n    ...$input.item.json,\n    cover_letter: coverLetter,\n    generated_at: new Date().toISOString()\n  }\n};"
      },
      "id": "parse-cover-letter",
      "name": "Parse Cover Letter",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [2220, 500]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent",
        "authentication": "predefinedCredentialType",
        "nodeCredentialType": "googleGeminiOAuth2Api",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"contents\": [{\n    \"parts\": [{\n      \"text\": \"You are an expert at filling out job application forms. Based on this job posting and candidate info, provide answers to common application questions.\\n\\n**CANDIDATE:**\\n{{ JSON.stringify($('Load Resume Data').item.json) }}\\n\\n**JOB:**\\nTitle: {{ $json.job_title }}\\nCompany: {{ $json.company }}\\nDescription: {{ $json.description.substring(0, 1000) }}\\n\\nProvide JSON with pre-filled answers for these common application fields:\\n{\\n  \\\"why_interested\\\": \\\"2-3 sentence answer about why interested in this role\\\",\\n  \\\"why_good_fit\\\": \\\"2-3 sentences on why you're a great fit\\\",\\n  \\\"relevant_experience\\\": \\\"Brief description of most relevant experience\\\",\\n  \\\"technical_expertise\\\": \\\"How technical skills apply to this role\\\",\\n  \\\"availability\\\": \\\"{{ $('Load Resume Data').item.json.availability }}\\\",\\n  \\\"salary_expectation\\\": \\\"{{ $('Load Resume Data').item.json.salary_expectation }}\\\",\\n  \\\"strengths\\\": [\\\"strength 1\\\", \\\"strength 2\\\", \\\"strength 3\\\"],\\n  \\\"why_leave_current\\\": \\\"Seeking new opportunities to apply technical and creative skills in growth-focused role\\\",\\n  \\\"questions_for_employer\\\": [\\\"question 1\\\", \\\"question 2\\\"]\\n}\\n\\nMake answers specific to THIS job and company.\"\n    }]\n  }],\n  \"generationConfig\": {\n    \"temperature\": 0.5,\n    \"maxOutputTokens\": 1500\n  }\n}",
        "options": {}
      },
      "id": "generate-application-answers",
      "name": "AI: Generate Application Form Answers",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [2000, 680],
      "credentials": {
        "googleGeminiOAuth2Api": {
          "id": "YOUR_CREDENTIAL_ID",
          "name": "Google Gemini API"
        }
      }
    },
    {
      "parameters": {
        "jsCode": "// Parse application answers\nconst response = JSON.parse($input.item.json.body);\nconst aiText = response.candidates[0].content.parts[0].text;\n\nlet jsonText = aiText;\nif (aiText.includes('```json')) {\n  jsonText = aiText.split('```json')[1].split('```')[0].trim();\n} else if (aiText.includes('```')) {\n  jsonText = aiText.split('```')[1].split('```')[0].trim();\n}\n\nconst applicationAnswers = JSON.parse(jsonText);\n\n// Get cover letter from previous node\nconst coverLetterData = $('Parse Cover Letter').item.json;\n\nreturn {\n  json: {\n    ...coverLetterData,\n    application_answers: applicationAnswers\n  }\n};"
      },
      "id": "combine-application-data",
      "name": "Combine All Application Data",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [2220, 680]
    },
    {
      "parameters": {
        "operation": "appendOrUpdate",
        "documentId": {
          "__rl": true,
          "value": "YOUR_GOOGLE_SHEET_ID",
          "mode": "list",
          "cachedResultName": "Job Application Tracker"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Sheet1"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "Date_Found": "={{ $now.toISO() }}",
            "Job_Title": "={{ $json.job_title }}",
            "Company": "={{ $json.company }}",
            "Location": "={{ $json.location }}",
            "Match_Score": "={{ $json.match_score }}",
            "Recommendation": "={{ $json.recommendation }}",
            "Job_URL": "={{ $json.job_url }}",
            "Status": "Ready to Apply",
            "Cover_Letter": "={{ $json.cover_letter }}",
            "Why_Interested": "={{ $json.application_answers.why_interested }}",
            "Why_Good_Fit": "={{ $json.application_answers.why_good_fit }}",
            "Salary": "={{ $json.salary }}"
          },
          "matchingColumns": [],
          "schema": []
        },
        "options": {}
      },
      "id": "log-to-sheets",
      "name": "📊 Save to Google Sheets Tracker",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.4,
      "position": [2440, 500]
    },
    {
      "parameters": {
        "operation": "create",
        "folderId": {
          "__rl": true,
          "value": "YOUR_GOOGLE_DRIVE_FOLDER_ID",
          "mode": "list",
          "cachedResultName": "Job Applications"
        },
        "name": "={{ $json.company }} - {{ $json.job_title }} - Application.txt",
        "options": {
          "mimeType": "text/plain"
        }
      },
      "id": "save-to-drive",
      "name": "💾 Save Application to Google Drive",
      "type": "n8n-nodes-base.googleDrive",
      "typeVersion": 3,
      "position": [2440, 680],
      "executeOnce": false
    },
    {
      "parameters": {},
      "id": "content-trigger",
      "name": "Content Creation Trigger",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [240, 1100]
    },
    {
      "parameters": {
        "rule": {
          "interval": [
            {
              "field": "hours",
              "hoursInterval": 8
            }
          ]
        }
      },
      "id": "content-schedule",
      "name": "Auto Content Ideas (8hrs)",
      "type": "n8n-nodes-base.scheduleTrigger",
      "typeVersion": 1.2,
      "position": [240, 1220]
    },
    {
      "parameters": {
        "content": "=## 🎣 FISHING BRAND CONTENT AUTOMATION\n\n**Your Brand Profile:**\n- Niche: Fishing Tackle & Gear\n- Platform: Shopify Drop Shipping\n- Assets: Large social media following + fishing footage library\n- Challenge: Winter = no new footage\n- Goal: Convert followers to customers by Christmas\n\n**Content Strategy:**\n1. Repurpose existing footage into new formats\n2. Educational content (gear reviews, tips, how-tos)\n3. User-generated content campaigns\n4. Behind-the-scenes (business journey)\n5. Holiday gift guides for anglers\n\n**Platforms:**\n- Instagram/TikTok: Short clips + product links\n- YouTube Shorts: Bite-sized tips\n- Pinterest: Product pins + fishing inspiration\n- Facebook Groups: Community engagement\n\nThis workflow generates:\n✅ Daily content ideas\n✅ Post captions with product links\n✅ Hashtag strategies\n✅ Trend-jacking opportunities\n✅ Auto-schedules to Buffer/Later",
        "height": 589.5238095238095,
        "width": 459.52380952380955
      },
      "id": "content-sticky",
      "name": "🎣 CONTENT AUTOMATION INFO",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [700, 1100]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "brand_name",
              "name": "brand_name",
              "value": "Your Fishing Tackle Brand",
              "type": "string"
            },
            {
              "id": "shopify_url",
              "name": "shopify_url",
              "value": "yourstore.myshopify.com",
              "type": "string"
            },
            {
              "id": "niche",
              "name": "niche",
              "value": "Fishing tackle, gear, and accessories for freshwater and saltwater fishing",
              "type": "string"
            },
            {
              "id": "target_audience",
              "name": "target_audience",
              "value": "Recreational fishermen, fishing enthusiasts, outdoor lovers aged 25-55",
              "type": "string"
            },
            {
              "id": "brand_voice",
              "name": "brand_voice",
              "value": "Authentic, knowledgeable, enthusiastic, community-focused, helpful",
              "type": "string"
            },
            {
              "id": "product_categories",
              "name": "product_categories",
              "value": "[\"rods\", \"reels\", \"lures\", \"tackle boxes\", \"fishing line\", \"hooks\", \"accessories\"]",
              "type": "string"
            },
            {
              "id": "content_library",
              "name": "content_library",
              "value": "Large library of fishing footage including catches, techniques, locations, gear demos",
              "type": "string"
            },
            {
              "id": "social_platforms",
              "name": "social_platforms",
              "value": "[\"Instagram\", \"TikTok\", \"Facebook\", \"YouTube\"]",
              "type": "string"
            },
            {
              "id": "current_season",
              "name": "current_season",
              "value": "Winter - limited new footage, focus on repurposing and educational content",
              "type": "string"
            },
            {
              "id": "urgency",
              "name": "urgency",
              "value": "Christmas sales push - 3 weeks to convert followers to customers",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "set-brand-data",
      "name": "Load Brand Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [460, 1100]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent",
        "authentication": "predefinedCredentialType",
        "nodeCredentialType": "googleGeminiOAuth2Api",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"contents\": [{\n    \"parts\": [{\n      \"text\": \"You are a viral social media content strategist for a fishing tackle e-commerce brand.\\n\\n**BRAND INFO:**\\nBrand: {{ $json.brand_name }}\\nNiche: {{ $json.niche }}\\nAudience: {{ $json.target_audience }}\\nVoice: {{ $json.brand_voice }}\\nProducts: {{ $json.product_categories }}\\nAssets: {{ $json.content_library }}\\nSeason: {{ $json.current_season }}\\nUrgency: {{ $json.urgency }}\\nStore: {{ $json.shopify_url }}\\n\\n**TASK:** Generate 7 HIGH-CONVERTING content ideas for THIS WEEK that:\\n1. Repurpose existing fishing footage (no new filming needed)\\n2. Drive traffic to Shopify store\\n3. Work in winter when fishing is slow\\n4. Leverage holiday shopping urgency\\n5. Are platform-specific (Instagram/TikTok/Facebook)\\n\\nFor EACH idea provide JSON:\\n{\\n  \\\"ideas\\\": [\\n    {\\n      \\\"day\\\": \\\"Monday\\\",\\n      \\\"platform\\\": \\\"Instagram/TikTok/Facebook\\\",\\n      \\\"content_type\\\": \\\"Reel/Story/Post\\\",\\n      \\\"hook\\\": \\\"Attention-grabbing first line\\\",\\n      \\\"concept\\\": \\\"What the content is about\\\",\\n      \\\"footage_needed\\\": \\\"