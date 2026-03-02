{
  "name": "AI Job Search Agent - Urgent",
  "nodes": [
    {
      "parameters": {},
      "id": "manual-trigger",
      "name": "Manual Trigger",
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [240, 300]
    },
    {
      "parameters": {
        "content": "=## Job Search Profile\n\n**Your Background:**\n- E-commerce experience (Shopify store owner)\n- Social media management (fishing content creator)\n- Technical skills: Docker, Docker Compose, MCP servers, n8n automation\n- Hardware experience: Raspberry Pi 5, AI acceleration (Hailo), Wyoming server setup\n- API Integration: Google Gemini, DeepSeek\n- Drop shipping business operations\n\n**What jobs to search for:**\n1. E-commerce Manager/Specialist\n2. Social Media Manager\n3. DevOps/Docker Administrator\n4. Marketing Automation Specialist\n5. Technical Product Manager\n6. Remote IT Support\n7. Content Creator/Manager\n\n**Location:** {{ $json.location || 'Remote + Local' }}\n**Urgency:** IMMEDIATE (Christmas deadline)\n**Work Type:** Full-time, Part-time, Contract, Freelance",
        "height": 464.79266347992797,
        "width": 389.76636532096534
      },
      "id": "sticky-note",
      "name": "Your Profile & Target Roles",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [240, 500]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "job_titles",
              "name": "job_titles",
              "value": "=[\n  \"E-commerce Manager\",\n  \"Social Media Manager\",\n  \"DevOps Engineer\",\n  \"Docker Administrator\",\n  \"Marketing Automation Specialist\",\n  \"Shopify Developer\",\n  \"Content Marketing Manager\",\n  \"Technical Product Manager\",\n  \"IT Support Specialist\",\n  \"Systems Administrator\",\n  \"n8n Automation Specialist\",\n  \"Remote Social Media Coordinator\"\n]",
              "type": "array"
            },
            {
              "id": "skills",
              "name": "skills",
              "value": "=\"Docker, Shopify, Social Media Marketing, E-commerce, Content Creation, API Integration, Linux, Raspberry Pi, Automation, n8n, Drop Shipping\"",
              "type": "string"
            },
            {
              "id": "remote_preference",
              "name": "remote_preference",
              "value": "=true",
              "type": "boolean"
            },
            {
              "id": "urgency",
              "name": "urgency",
              "value": "=\"IMMEDIATE\"",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "set-profile",
      "name": "Set Your Profile Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [460, 300]
    },
    {
      "parameters": {
        "url": "https://www.indeed.com/jobs",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "q",
              "value": "={{ $json.job_titles[0] }}"
            },
            {
              "name": "l",
              "value": "Remote"
            },
            {
              "name": "fromage",
              "value": "1"
            }
          ]
        },
        "options": {}
      },
      "id": "indeed-search",
      "name": "Indeed Job Search",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [900, 180]
    },
    {
      "parameters": {
        "url": "https://remotive.com/api/remote-jobs",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "search",
              "value": "=ecommerce social media devops"
            },
            {
              "name": "limit",
              "value": "50"
            }
          ]
        },
        "options": {}
      },
      "id": "remotive-api",
      "name": "Remotive Remote Jobs API",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [900, 300]
    },
    {
      "parameters": {
        "url": "https://www.themuse.com/api/public/jobs",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "category",
              "value": "Engineering,Marketing"
            },
            {
              "name": "level",
              "value": "Entry Level,Mid Level"
            },
            {
              "name": "page",
              "value": "0"
            }
          ]
        },
        "options": {}
      },
      "id": "themuse-api",
      "name": "The Muse Jobs API",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [900, 420]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "job_title",
              "name": "job_title",
              "value": "={{ $json.title || $json.job_title || $json.name }}",
              "type": "string"
            },
            {
              "id": "company",
              "name": "company",
              "value": "={{ $json.company || $json.company_name || 'Unknown' }}",
              "type": "string"
            },
            {
              "id": "location",
              "name": "location",
              "value": "={{ $json.location || $json.candidate_required_location || 'Remote' }}",
              "type": "string"
            },
            {
              "id": "url",
              "name": "url",
              "value": "={{ $json.url || $json.job_url || $json.link || 'N/A' }}",
              "type": "string"
            },
            {
              "id": "description",
              "name": "description",
              "value": "={{ $json.description || $json.job_description || '' }}",
              "type": "string"
            },
            {
              "id": "posted_date",
              "name": "posted_date",
              "value": "={{ $json.publication_date || $json.posted || $now }}",
              "type": "string"
            },
            {
              "id": "source",
              "name": "source",
              "value": "={{ $node.name }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "normalize-jobs",
      "name": "Normalize Job Data",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [1120, 300]
    },
    {
      "parameters": {
        "resource": "chat",
        "operation": "create",
        "model": {
          "__rl": true,
          "value": "gemini-1.5-flash",
          "mode": "list",
          "cachedResultName": "gemini-1.5-flash"
        },
        "prompt": {
          "messages": [
            {
              "content": "=You are a job matching AI assistant. Analyze this job and rate it 0-100 based on match to candidate profile.\n\n**Candidate Profile:**\n- Skills: Docker, Shopify, Social Media Marketing, E-commerce, Content Creation, API Integration, Linux, Raspberry Pi, Automation, n8n, Drop Shipping\n- Experience: E-commerce store owner, social media content creator, technical automation\n- Urgency: IMMEDIATE need (Christmas deadline)\n\n**Job Details:**\nTitle: {{ $json.job_title }}\nCompany: {{ $json.company }}\nLocation: {{ $json.location }}\nDescription: {{ $json.description.substring(0, 1000) }}\n\nProvide response in this exact JSON format:\n{\n  \"match_score\": <0-100>,\n  \"reasoning\": \"<why this matches or doesn't>\",\n  \"key_matches\": [\"skill1\", \"skill2\"],\n  \"concerns\": [\"concern1\", \"concern2\"],\n  \"action\": \"APPLY_NOW\" or \"REVIEW\" or \"SKIP\",\n  \"quick_tips\": \"<application advice>\"\n}",
              "role": "user"
            }
          ]
        },
        "options": {
          "temperature": 0.3
        }
      },
      "id": "gemini-analyze",
      "name": "Gemini AI Job Analyzer",
      "type": "@n8n/n8n-nodes-langchain.lmChatGoogleGemini",
      "typeVersion": 1.1,
      "position": [1340, 300],
      "credentials": {
        "googleGeminiOAuth2Api": {
          "id": "YOUR_GEMINI_CREDENTIAL_ID",
          "name": "Google Gemini API"
        }
      }
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
              "id": "high-match",
              "leftValue": "={{ $json.match_score }}",
              "rightValue": "70",
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
      "name": "Filter High Matches (70+)",
      "type": "n8n-nodes-base.filter",
      "typeVersion": 2,
      "position": [1560, 300]
    },
    {
      "parameters": {
        "operation": "create",
        "base": {
          "__rl": true,
          "value": "appXXXXXXXXXXXXXX",
          "mode": "list",
          "cachedResultName": "Job Applications Tracker"
        },
        "table": {
          "__rl": true,
          "value": "tblXXXXXXXXXXXXXX",
          "mode": "list",
          "cachedResultName": "Applications"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "Job Title": "={{ $json.job_title }}",
            "Company": "={{ $json.company }}",
            "Location": "={{ $json.location }}",
            "URL": "={{ $json.url }}",
            "Match Score": "={{ $json.match_score }}",
            "Source": "={{ $json.source }}",
            "Status": "To Apply",
            "Date Found": "={{ $now.toISO() }}",
            "Action": "={{ $json.action }}",
            "Notes": "={{ $json.quick_tips }}"
          },
          "matchingColumns": [],
          "schema": []
        },
        "options": {}
      },
      "id": "airtable-log",
      "name": "Log to Airtable (Optional)",
      "type": "n8n-nodes-base.airtable",
      "typeVersion": 2,
      "position": [1780, 200],
      "notes": "Replace with your Airtable base/table IDs or use Google Sheets",
      "disabled": true
    },
    {
      "parameters": {
        "operation": "appendOrUpdate",
        "documentId": {
          "__rl": true,
          "value": "YOUR_GOOGLE_SHEET_ID",
          "mode": "list",
          "cachedResultName": "Job Tracker"
        },
        "sheetName": {
          "__rl": true,
          "value": "Sheet1",
          "mode": "list",
          "cachedResultName": "Sheet1"
        },
        "columns": {
          "mappingMode": "autoMapInputData",
          "value": {},
          "matchingColumns": [],
          "schema": []
        },
        "options": {}
      },
      "id": "google-sheets-log",
      "name": "Log to Google Sheets",
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.4,
      "position": [1780, 300]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "summary",
              "name": "summary",
              "value": "=## 🎯 HIGH PRIORITY JOB MATCHES FOUND!\n\n**Total Jobs Analyzed:** {{ $input.all().length }}\n**High Matches (70+):** {{ $input.all().filter(j => j.json.match_score >= 70).length }}\n\n{% for job in $input.all().slice(0, 10) %}\n---\n### {{ loop.index }}. {{ job.json.job_title }} @ {{ job.json.company }}\n**Match Score:** {{ job.json.match_score }}/100 ⭐\n**Location:** {{ job.json.location }}\n**Action:** {{ job.json.action }}\n**Why it matches:** {{ job.json.reasoning }}\n**Apply here:** {{ job.json.url }}\n\n{% endfor %}\n\n🚨 **URGENT:** Christmas is 3 weeks away. Focus on \"APPLY_NOW\" jobs first!",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "format-summary",
      "name": "Format Summary Report",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.3,
      "position": [1780, 420]
    },
    {
      "parameters": {
        "fromEmail": "your-email@gmail.com",
        "toEmail": "your-email@gmail.com",
        "subject": "🚨 URGENT: High-Match Jobs Found - Apply Today!",
        "emailType": "html",
        "message": "={{ $json.summary }}",
        "options": {}
      },
      "id": "send-email",
      "name": "Email Job Alert",
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 2.1,
      "position": [2000, 300],
      "disabled": true,
      "notes": "Enable this if you want email alerts"
    },
    {
      "parameters": {
        "content": "=## 🎣 BONUS: Quick Shopify Sales Boost\n\nWhile job hunting, try these to get customers:\n\n1. **Post your fishing footage NOW**\n   - \"Best catches of 2024\" compilation\n   - Winter fishing prep tips\n   - Link to your store in bio\n\n2. **Run Instagram/TikTok ads** ($5-10/day)\n   - Target: Fishing enthusiasts in your area\n   - Show popular tackle from your store\n\n3. **Holiday Bundle Deal**\n   - \"Winter Fishing Kit\" - 3 items, 20% off\n   - Create urgency: \"12 Days of Christmas Deals\"\n\n4. **Contact your followers directly**\n   - DM top engagers with exclusive discount\n   - \"Hey! Started a fishing tackle shop...\"\n\n5. **Facebook Fishing Groups**\n   - Share expertise + subtle store mention\n   - Offer group-exclusive discount code\n\nYou have the audience already - monetize it!",
        "height": 519.8329355608591,
        "width": 386.83783783783787
      },
      "id": "shopify-tips",
      "name": "Shopify Quick Win Tips",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [240, 1000]
    },
    {
      "parameters": {
        "mode": "combine",
        "combinationMode": "multiplex",
        "options": {}
      },
      "id": "merge-jobs",
      "name": "Merge All Job Sources",
      "type": "n8n-nodes-base.merge",
      "typeVersion": 3,
      "position": [1120, 300]
    },
    {
      "parameters": {
        "operation": "split",
        "fieldToSplitOut": "jobs",
        "options": {}
      },
      "id": "split-remotive",
      "name": "Split Remotive Jobs Array",
      "type": "n8n-nodes-base.itemLists",
      "typeVersion": 3.3,
      "position": [900, 540]
    }
  ],
  "connections": {
    "Manual Trigger": {
      "main": [
        [
          {
            "node": "Set Your Profile Data",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Set Your Profile Data": {
      "main": [
        [
          {
            "node": "Indeed Job Search",
            "type": "main",
            "index": 0
          },
          {
            "node": "Remotive Remote Jobs API",
            "type": "main",
            "index": 0
          },
          {
            "node": "The Muse Jobs API",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Indeed Job Search": {
      "main": [
        [
          {
            "node": "Merge All Job Sources",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Remotive Remote Jobs API": {
      "main": [
        [
          {
            "node": "Split Remotive Jobs Array",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Split Remotive Jobs Array": {
      "main": [
        [
          {
            "node": "Merge All Job Sources",
            "type": "main",
            "index": 1
          }
        ]
      ]
    },
    "The Muse Jobs API": {
      "main": [
        [
          {
            "node": "Merge All Job Sources",
            "type": "main",
            "index": 2
          }
        ]
      ]
    },
    "Merge All Job Sources": {
      "main": [
        [
          {
            "node": "Normalize Job Data",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Normalize Job Data": {
      "main": [
        [
          {
            "node": "Gemini AI Job Analyzer",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Gemini AI Job Analyzer": {
      "main": [
        [
          {
            "node": "Filter High Matches (70+)",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Filter High Matches (70+)": {
      "main": [
        [
          {
            "node": "Log to Google Sheets",
            "type": "main",
            "index": 0
          },
          {
            "node": "Log to Airtable (Optional)",
            "type": "main",
            "index": 0
          },
          {
            "node": "Format Summary Report",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Format Summary Report": {
      "main": [
        [
          {
            "node": "Email Job Alert",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "settings": {
    "executionOrder": "v1"
  }
}