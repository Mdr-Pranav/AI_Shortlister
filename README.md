# Intelligent Shortlister

An AI-powered resume screening and candidate shortlisting pipeline that automatically matches candidates to job positions using Google's Gemini AI.

## Overview

The Intelligent Shortlister is a sophisticated pipeline that automates the initial screening of job candidates by analyzing their resumes against predefined job descriptions. It uses Google's Gemini AI to make intelligent matching decisions while maintaining flexibility in the evaluation process.

## Features

- **Multi-Job Support**: Can handle multiple job descriptions simultaneously
- **Flexible Matching**: Configurable strictness levels for candidate evaluation
- **Smart Document Processing**: Supports both PDF and DOCX resume formats
- **Organized Output**: Automatically sorts candidates into role-specific folders
- **Detailed Analysis**: Provides reasoning for shortlisting decisions
- **Error Handling**: Robust error management and rate limiting protection
- **Detailed Reporting**: Optional in-depth analysis of matched candidates

## Pipeline Structure

1. **Installation and Setup** (Block 1)

   - Installs required libraries
   - Sets up Google Gemini API
   - Configures environment

2. **Base Configuration** (Block 2-3)

   - Defines base paths and folders
   - Sets up company context
   - Configures job descriptions
   - Controls pipeline behavior (flexibility, explanations)

3. **Directory Management** (Block 4)

   - Creates dynamic folder structure based on job titles
   - Manages output directories for:
     - Shortlisted candidates (per role)
     - Non-shortlisted candidates
     - Error cases

4. **Helper Functions** (Block 5)

   - Resume text extraction (PDF/DOCX)
   - File management utilities
   - Rate limit handling
   - Flexibility level management

5. **Main Pipeline** (Block 6)

   - Sequential resume processing
   - Job matching analysis
   - Candidate sorting
   - Result reporting

6. **Detailed Analysis** (Block 7)
   - In-depth candidate assessment
   - Strength/weakness analysis
   - Interview recommendations

## Configuration Options

### Shortlisting Flexibility Levels

- **Strict**: Candidates must meet almost all required qualifications
- **Balanced**: Candidates must meet most core requirements or compensate with strong relevant experience
- **Flexible**: Considers high-potential candidates with transferable skills

### Pipeline Controls

```python
Show_Explanation = True  # Show reasoning for decisions
Clean_Folder = True     # Clean output folders before running
SHORTLISTING_FLEXIBILITY = 'Flexible'  # Strictness level
```

## Folder Structure

```
Applicants/
├── {job_title_1}/
│   └── shortlisted/
├── {job_title_2}/
│   └── shortlisted/
├── not_shortlisted_for_any_role/
└── errors/
```

## Requirements

- Python 3.x
- Google Gemini API key
- Required Python packages:
  - google-generativeai
  - pymupdf (for PDF processing)
  - python-docx (for DOCX processing)

## Setup Instructions

1. Install required packages:

   ```bash
   pip install -q -U google-generativeai pymupdf python-docx
   ```

2. Configure your API key:

   ```python
   API_KEY = "your_gemini_api_key_here"
   ```

3. Set up your base folder path:

   ```python
   APPLICANTS_FOLDER = 'path/to/your/applicants/folder'
   ```

4. Define your job descriptions in the `JOB_DESCRIPTIONS` list

## Usage

1. Place all candidate resumes in the `APPLICANTS_FOLDER`
2. Configure job descriptions and flexibility settings
3. Run the pipeline
4. Check the output folders for sorted candidates
5. Optionally run detailed analysis on specific candidates

## Output

The pipeline produces:

- Sorted resumes in appropriate folders
- Decision explanations (if enabled)
- Detailed candidate reports (on demand)

## Error Handling

The pipeline includes robust error handling for:

- API rate limits (with exponential backoff)
- File reading errors
- Invalid file formats
- Empty files
- JSON parsing errors

## Best Practices

1. **Resume Format**

   - Use PDF or DOCX formats
   - Ensure files are not corrupted
   - Maintain consistent naming conventions

2. **Job Descriptions**

   - Be specific about requirements
   - Include both required and preferred qualifications
   - Maintain consistent formatting

3. **Pipeline Usage**
   - Start with a test batch of resumes
   - Monitor the explanations to tune flexibility
   - Regularly check the errors folder

## Limitations

- Currently supports only PDF and DOCX formats
- Requires Google Gemini API access
- Processing speed depends on API rate limits
- Limited to text-based analysis (no image processing)

## Contributing

Feel free to submit issues and enhancement requests!
