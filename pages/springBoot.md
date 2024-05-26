- @Value使用
	- ```java
	  ./pojo/EmailProperties
	  @Component
	  public class EmailProperties {
	      @Value("${email.user}")
	      public String user;
	  }
	  
	  ./controller/
	  @RestController
	  public class EmailController {
	  
	      @Autowired
	      private EmailProperties emailProperties;
	  
	      @RequestMapping("/sendemail")
	      public String sendemail() {
	      return "sendemail:"+emailProperties.user;
	  
	      }
	  }
	  ```