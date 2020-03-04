package webdriver;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.Alert;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;


public class JavaTpoint {

	public static void main(String[] args) {

		System.setProperty("webdriver.chrome.driver", System.getProperty("user.dir")+"\\src\\main\\resources\\Driver\\chromedriver.exe");
		WebDriver driver = new ChromeDriver();
		driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
		
		driver.get("http://automationpractice.com/index.php?controller=authentication");
		driver.manage().window().maximize();  
		System.out.println(driver.getTitle());
		
	    driver.findElement(By.xpath("//a[@class='login']")).click();
		driver.findElement(By.xpath("//*[@id=\"email\"]")).sendKeys("training.qaprep@gmail.com");
		driver.findElement(By.xpath("//input[@id='passwd']")).sendKeys("Testing123");
		driver.findElement(By.xpath("//button[@id='SubmitLogin']")).click();
		Actions act=new Actions(driver);
		WebElement women=driver.findElement(By.xpath("//a[@title='Women']"));
		act.moveToElement(women).perform();
		driver.findElement(By.xpath("//li[1]/a[@title='T-shirts']")).click();

		
		Actions act2=new Actions(driver);
		WebElement product=driver.findElement(By.xpath("//ul/li/div[@class='product-container']"));
      
		act2.moveToElement(product).perform();
		driver.findElement(By.xpath("//a/span[contains(text(),'More')]")).click();
		driver.findElement(By.xpath("//i[@class='icon-plus']")).click();
		Select drpSize=new Select(driver.findElement(By.xpath("/html//select[@id='group_1']")));
		drpSize.selectByVisibleText("L");
		driver.findElement(By.name("Orange")).click();
		driver.findElement(By.name("Submit")).click();
		
		
		driver.findElement(By.xpath("/html//div[@id='layer_cart']//a[@title='Proceed to checkout']/span")).click();

		driver.findElement(By.xpath("//div[@id='center_column']//a[@title='Proceed to checkout']/span")).click();
		driver.findElement(By.xpath("//div[@id='center_column']/form[@action='http://automationpractice.com/index.php?controller=order']//button/span")).click();
		driver.findElement(By.xpath("/html//input[@id='cgv']")).click(); 
		driver.findElement(By.xpath("//form[@id='form']//button[@name='processCarrier']/span")).click(); 
		driver.findElement(By.xpath("/html//div[@id='HOOK_PAYMENT']//a[@title='Pay by bank wire']/span[.='(order processing will be longer)']")).click(); 
		driver.findElement(By.xpath("//p[@id='cart_navigation']//span")).click();
		
		//Assert the text to confirm purchase
	    String bodyText = driver.findElement(By.tagName("body")).getText();
	    
	    driver.quit();
	
		
			}

}
