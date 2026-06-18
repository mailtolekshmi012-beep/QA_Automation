# Practice Software Testing Automation

## Automation Framework

- Selenium
- Python
- Pytest

## Test Cases Automated

1. Verify Homepage Loads Successfully
2. Verify Product Search Using Valid Keyword (Hammer)
3. Verify Product Search Using Invalid Keyword (AAA)

## Setup

Install Python 3.x

Install dependencies:

```
pip install -r requirements.txt
```

## Execute Tests

```
pytest tests

Test Case 1 - Homepage Load

# tests/test_homepage.py

from selenium import webdriver
from selenium.webdriver.common.by import By
import time

def test_homepage_load():

    driver = webdriver.Chrome()

    driver.get("https://practicesoftwaretesting.com")

    driver.maximize_window()

    assert "Practice Software Testing" in driver.title

    time.sleep(3)

    driver.quit()

Test Case 2 - Search Valid Product (Hammer)

# tests/test_search_valid.py

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

def test_search_hammer():

    driver = webdriver.Chrome()

    driver.get("https://practicesoftwaretesting.com")

    driver.maximize_window()

    time.sleep(2)

    search_box = driver.find_element(By.CSS_SELECTOR, "input[data-test='search-query']")

    search_box.send_keys("Hammer")

    search_box.send_keys(Keys.ENTER)

    time.sleep(3)

    driver.save_screenshot("screenshots/hammer_search.png")

    assert "Hammer" in driver.page_source

    driver.quit()


Test Case 3 - Search Invalid Product (AAA)

# tests/test_search_invalid.py

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

def test_search_invalid_product():

    driver = webdriver.Chrome()

    driver.get("https://practicesoftwaretesting.com")

    driver.maximize_window()

    time.sleep(2)

    search_box = driver.find_element(By.CSS_SELECTOR, "input[data-test='search-query']")

    search_box.send_keys("AAA")

    search_box.send_keys(Keys.ENTER)

    time.sleep(3)

    driver.save_screenshot("screenshots/no_product_found.png")

    assert "There are no products found" in driver.page_source

    driver.quit()

## Website Tested

https://practicesoftwaretesting.com



