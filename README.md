# stepik_auto_tests_course
домашние задания к курсу
https://stepik.org/lesson/187065/step/7?unit=161976


from selenium import webdriver
from selenium.webdriver.common.by import By
import time
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import math
import pyperclip as pc


def calc(): #решалка задания
    driver.find_element(By.CLASS_NAME, 'form-control').send_keys(
        str(math.log(abs(12 * math.sin(int(
            driver.find_element(By.ID, 'input_value').text))))))
    driver.find_element(By.ID, "solve").click()
    stepikCalc()

def stepikCalc():
    pc.copy(driver.switch_to.alert.text.split(': ')[-1])  # сохранить в буфер калькуляцию

def returnTextInElement(BySearch, element, text, time):
    if BySearch == 'id' or 'ID':                                                 #ждем когда текст будет 100 в прайсе
        return WebDriverWait(driver, time).until(EC.text_to_be_present_in_element((By.ID, element), text))

try:
    link = "http://suninjuly.github.io/explicit_wait2.html"
    driver = webdriver.Chrome('E:\Selenium\chromedriver.exe')
    driver.implicitly_wait(5)
    driver.get(link)

    returnTextInElement('ID', 'price', '100', 15)
    driver.find_element(By.ID, 'book').click()
    calc()

finally:
    time.sleep(5000)
    driver.quit()