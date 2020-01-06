## 如何在selenium java中使隐藏元素可显示和可点击？





有以下元素：

```javascript
<table class="dijit " data-dojo-attach-point="_buttonNode" cellspacing="0" cellpadding="0" role="lbox" aria-haspopup="true" tabindex="0" id="POS_domain" data-id="domain" widgetid="POS_domain" aria-expanded="false" aria- invalid="false" style="user-select: none;" popupactive="true" aria-owns="POS_domain">
    <tbody role="presentation">
        <tr role="presentation">
            <td class="dijitReset" role="presentation">
                <div class="dijitReset Text" data-dojo-attach-point="container" role="presentation">
                    <span role="option" aria-selected="true" class="dijitLabel ">adrija</span>
                </div>
                <div class="dijitContainer">
                    <input class="dijitInner" value="Χ " type="text" tabindex="-1" readonly="readonly" role="presentation">
                </div>
                <input type="hidden" data-dojo-attach-point="vn" value="adrija" hidden="true">
            </td>
            <td class="dijitArrowButtonContainer" data-dojo-attach-point="titleNode" role="presentation">
                <input class="dijitInner" value="▼ " type="text" tabindex="-1" readonly="readonly" role="presentation">
            </td>
        </tr>
    </tbody>
</table>
```

上面的元素是下拉列表的元素并被隐藏。我写的代码是：

```javascript
private WebElement domainDropdown = Driver.driver.findElement(By.id("POS_domain"));
domainDropdpwn.click();
private WebElement adrija = Driver.driver.findElement(By.xpath("//input[@value='adrija' and @data-dojo-attach-point='vn']"));
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("arguments[0].click();", adrija);
```

期望的``标签具有的属性`type="hidden"`和`hidden="true"`，所以`click()`可以使用以下溶液中的元件上：



```javascript
//driver being an instance of WebDriver
new WebDriverWait(driver, 20).until(ExpectedConditions.elementToBeClickable(By.xpath("//table[@class='dijit ' and @id='POS_domain']"))).click();
WebElement my_adrija = driver.findElement(By.xpath("//input[@value='adrija' and @data-dojo-attach-point='vn']"));
((JavascriptExecutor)driver).executeScript("arguments[0].removeAttribute('hidden')", my_adrija)
((JavascriptExecutor)driver).executeScript("arguments[0].setAttribute('type','text')", my_adrija)
WebElement my_new_adrija = new WebDriverWait(driver, 20).until(ExpectedConditions.elementToBeClickable(By.xpath("//input[@value='adrija' and @data-dojo-attach-point='vn']")));
((JavascriptExecutor)driver).executeScript("arguments[0].click();", my_new_adrija);
```

