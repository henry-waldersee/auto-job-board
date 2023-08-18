options = Options()
options.add_argument("--headless=new") #this makes it so that the we can run a "headless" browser (no GUI)
driver = webdriver.Chrome(options=options)

url_uk = 'https://johngannonblog.com/venture-capital-jobs-in-london/'
url_europe = 'https://johngannonblog.com/venture-capital-jobs-in-europe/'

driver.get(url_europe)

#Script to delete popups!
#popups = driver.find_elements(By.CLASS_NAME, "rm-close")
#if len(popups) > 0:
#   driver.find_element(By.CLASS_NAME, "rm-close").click()


#script to click on link:
#driver.find_element(By.XPATH, '//a[text()="Venture Capital Jobs and Internships in London"]').click()


ul_positions  = driver.find_element(By.CSS_SELECTOR, 'ul.job_listings')

#we cannot iterate through ul positions, as it is one block of text. 
#Therefore, we are going to create different lists containing the title, the link to the job description and the time it was posted.

job_position_name = ul_positions.find_elements(By.TAG_NAME, 'h3')
job_position_date = ul_positions.find_elements(By.CSS_SELECTOR, 'time')
job_position_link = ul_positions.find_elements(By.TAG_NAME,   'a')

entries = []

for date name, date, link in zip(job_position_name, job_position_date, job_position_link):

    entries.append({'Position': name.text,
                    'Uploaded': date.get_attribute('datetime'), 
                    'Descript': link.get_attribute('href')})

entries_df = pd.DataFrame(entries)

entries_df
