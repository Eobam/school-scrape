# School Scrape
 
A Python script that scrapes school websites to extract STEM teacher information and exports it to a CSV file.
 
## Features
 
- **Automatic STEM Detection**: Identifies science, math, and STEM teachers based on keywords
- **Information Extraction**: Pulls names, emails, phone numbers, roles, and departments
- **Site Navigation**: Automatically finds and scrapes staff/faculty pages
- **CSV Export**: Saves all data to an organized CSV file
- **Deduplication**: Removes duplicate entries
- **Respectful Scraping**: Includes delays between requests
## Installation
 
### Requirements
- Python 3.7+
- `requests` library
- `beautifulsoup4` library
### Setup
 
1. Install required dependencies:
```bash
pip install requests beautifulsoup4
```
 
2. Download the script:
```bash
# The script is in school_teacher_scraper.py
```
 
## Usage
 
### Basic Usage
```bash
python school_teacher_scraper.py https://www.schoolname.edu
```
 
This will create a file called `school_teachers.csv` in the current directory.
 
### Custom Output Filename
```bash
python school_teacher_scraper.py https://www.schoolname.edu my_output.csv
```
 
## Output Format
 
The CSV file contains the following columns:
 
| Column | Description |
|--------|-------------|
| **Name** | Teacher's full name |
| **Email** | Email address |
| **Phone** | Phone number (if found) |
| **Role** | Job title/subject area |
| **Department** | STEM department (Science, Math, Technology, Engineering) |
| **School URL** | The school website URL |
 
### Example Output
 
```
Name,Email,Phone,Role,Department,School URL
"John Smith","j.smith@school.edu","555-123-4567","High School Physics Teacher","Science","https://www.school.edu"
"Jane Doe","jane.doe@school.edu","555-123-4568","AP Computer Science Teacher","Technology","https://www.school.edu"
```
 
## How It Works
 
1. **Fetches the main school page** and parses the HTML
2. **Identifies staff/faculty pages** by looking for common navigation links
3. **Scrapes each page** looking for teacher information cards or listings
4. **Extracts STEM teachers** using keyword matching (science, math, engineering, etc.)
5. **Parses contact information** (emails, phone numbers)
6. **Removes duplicates** and exports to CSV
## STEM Keywords Detected
 
The script identifies teachers in the following areas:
- **Science**: Biology, Chemistry, Physics, Earth Science, Environmental Science, Anatomy, Physiology
- **Math**: Algebra, Geometry, Calculus, Statistics
- **Technology**: Computer Science, Programming, Coding, IT, Digital Literacy
- **Engineering**: Engineering, Robotics, Technology
## Notes and Limitations
 
⚠️ **Important Considerations:**
 
1. **Website Structure Varies**: School websites have different layouts. The script works best with schools that have organized staff directories.
2. **Success Rates**: Effectiveness depends on:
   - How clearly teachers' roles are labeled
   - Whether contact information is publicly available
   - The website's HTML structure
3. **Terms of Service**: Always check the school's website terms of service before scraping. Some sites may have robots.txt restrictions.
4. **Rate Limiting**: The script includes 0.5-second delays between requests to be respectful.
5. **Manual Verification**: It's recommended to verify the extracted data, as automatic parsing can sometimes miss or misinterpret information.
## Troubleshooting
 
### "Failed to fetch main page"
- Check that the URL is correct and accessible
- Try with `http://` or `https://` explicitly
- Check if the site blocks bots
### "No STEM teachers found"
- The school's website may not have a public staff directory
- Teacher information might be on a different page or domain
- Check the website manually to see if contact info is available
### Getting fewer results than expected
- Some schools keep staff info in PDFs or JavaScript-rendered content (this script handles HTML only)
- Contact information may be restricted/private
- The keywords might not match your school's terminology
## Enhancing Results
 
To improve results for a specific school:
 
1. Manually identify the staff directory URL and update the script
2. Add school-specific keywords to `STEM_KEYWORDS`
3. Inspect the HTML structure and add custom parsing for that school's layout
## Example Commands
 
```bash
# Scrape a school district
python school_teacher_scraper.py https://www.example-school-district.edu teachers.csv
 
# Scrape a specific school
python school_teacher_scraper.py https://www.middleschool123.edu middle_school_stem.csv
 
# Scrape a college/university STEM department
python school_teacher_scraper.py https://www.university.edu/stem faculty.csv
```
 
## Support
 
If you encounter issues with a specific school website:
1. Check that the URL is correct
2. Manually verify that staff information is publicly available
3. Inspect the website's HTML to see if the structure matches what the script expects
4. Consider reaching out to the school directly if info isn't public
## Legal Disclaimer
 
Use this tool responsibly and in accordance with the website's terms of service. Always respect robots.txt files and rate limits. This tool is for educational purposes.