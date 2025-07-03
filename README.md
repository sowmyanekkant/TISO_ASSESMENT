#Automation_Script

package org.example.my_app;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class AppTest {
      public static void main(String[] args) {
        // Initialize WebDriver
        WebDriver driver = new ChromeDriver();

        try {
            // Navigate to the website
            driver.get("https://pwiddy.interview.tisostudio.com/");

            // Search for the restaurant
            WebElement searchBox = driver.findElement(By.cssSelector("input[type='text']")); // Replace with actual locator
            searchBox.sendKeys("West, Mayer and Wintheiser");
            Thread.sleep(6000);
            
            WebElement searchButton = driver.findElement(By.className("button[type='submit']")); // Replace with actual locator
            searchButton.click();
            Thread.sleep(6000);
            
            // Select the restaurant from search results
            WebElement restaurantLink = driver.findElement(By.className("flex justify-between items-start"));
            restaurantLink.click();
            Thread.sleep(6000);

            // Add a few items to the cart
            WebElement addItem1 = driver.findElement(By.className("font-medium text-gray-900")); // Replace with actual locator
            addItem1.click();
            Thread.sleep(6000);

            WebElement addItem2 = driver.findElement(By.className("font-medium text-gray-900")); // Replace with actual locator
            addItem2.click();
            Thread.sleep(6000);

            // 7. Go to cart
            WebElement cartButton = driver.findElement(By.className("absolute -top-2 -right-2 bg-white text-red-600 rounded-full w-6 h-6 flex items-center justify-center text-sm font-bold")); // Replace with actual locator
            cartButton.click();
            Thread.sleep(6000);
            
            WebElement proceedCheckoutButton = driver.findElement(By.className("mt-6 w-full bg-red-600 text-white py-3 px-4 rounded-md hover:bg-red-700 transition focus:outline-none focus:ring-2 focus:ring-red-500 font-medium"));
              // Click on the "Proceed to Checkout" button
            proceedCheckoutButton.click();
            Thread.sleep(6000);
         //  Click to select "Cash"
            WebElement cashPaymentOption = driver.findElement(By.className("text-xl font-semibold text-gray-900 mb-6"));
            cashPaymentOption.click();
            Thread.sleep(6000);
            //select cashradio option
            WebElement cashRadioInput = driver.findElement(By.id("cash"));
            if (cashRadioInput.isSelected()) {
                System.out.println("Cash payment option selected successfully.");
            } else {
                System.out.println("Failed to select Cash payment option.");
                //click on place order button
                WebElement placeOrderButton = driver.findElement(By.className("mt-6 w-full py-3 px-4 rounded-md font-medium text-white focus:outline-none focus:ring-2 focus:ring-red-500 bg-red-600 hover:bg-red-700 transition")); // Replace with actual locator
                placeOrderButton.click();
                Thread.sleep(6000);

                //  Verify success message
                WebElement successMessage = driver.findElement(By.className("text-3xl font-bold text-gray-900 mb-2")); // Replace with actual locator
                if (successMessage.isDisplayed()) {
                    System.out.println("Test Passed: Order placed successfully.");
                } else {
                    System.out.println("Test Failed: Order was not placed.");
                }
            	    // . Close the browser
                driver.quit();
            }
     
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
        }
    }
}

    
 
