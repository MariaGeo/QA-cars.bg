 ### 1. Feature: Searching ###

 #### User story: ####  
 > As a user who is interested in buying cars
 
 > I want to search for preferred Make and Model  
 
 > So that I can get available deals at “http://www.cars.bg”
 
##### Background: #####
````html
Given I navigate to the Home page - http://www.cars.bg
  And I select “търсене“
  And I select Марка drop-down
````

####### 1.1.  `Scenario:` ####### User is able to search by preferred Make 
 
        When I choose Марка “Subaru”
        Then I should see all cars "Subaru” 

 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |
 
** 1.2. `Scenario:` **  User is NOT able to search by 2 or more preferred Make
 
 
         When I choose Марка “VW”
          And I choose also Марка “Volvo”
         Then I should see only the last chosen Mark- “Volvo” 

| Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |

** 1.3. `Scenario:` ** User is able to search by 2 or more preferred Models of preferred Make 

          When I choose Марка “ZAZ”
           And I choose Model “965” and “968”
          Then I should see only the offers with Models “965” and “968” 

 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |

** 1.4. `Scenario:` ** User is able to choose another preferred Model after he has already viewed  one Model

         When I choose Марка 'UAZ'
          And I choose from Модел drop-down “452”    
         Then I should see all offers with UAZ 452
         When I select “go back” button       
         Then I should see  all Models of UAZ in Модел drop-down
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Failed | Not run | Failed |    



** 1.5. `Scenario:` ** User is able to see preferred Model on preferred Make 

          When I choose Марка 'Bentley'
           And I choose from Модел drop-down “Continental”            
          Then I should see all cars 'Bentley Continental” 
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |

** 1.6. `Scenario:` ** User is able to see all detailed information about preferred Mark and Model.
 
         When I choose Марка 'Subaru'
          And I choose from Модел drop-down “OUTBACK”    
         Then I should see  all offers with Subaru OUTBACK
         When I select one offer       
         Then I should see all detailed information about the preferred car.

 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed 

** 1.7. `Scenario:` ** User is NOT able to see Models in „Модел“drop-down, which are not of the preferred Make car.

         When I choose Марка 'ZAZ'
          And I choose from Модел drop-down “965”    
         Then I should see all offers with ZAZ 965
         When I select “Търсене” button, which is up and right.
          And I select Марка „Suzuki“
          And I select Модел “Alto”  
         Then I should see all offers with Suzuki Alto
         When I select “go back” button                   
         Then I should see on the Mark drop-down - Suzuki and on the Models drop-down –the Models of Suzuki
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Failed| Not run | Passed 
        
------------------------------------------------------------------


### 2. Feature: Register ###
#### User story: ####
> As a user who is interested in  cars

> I want to make a registration 

> So that I can have my account.

##### Background: #####
````html
        Given I navigate to the Home page – http://www.cars.bg
          And I go to “Меню” and select "Вход/Регистрация”
          And I click on “Частно лице”
          And select „Регистрация“ 
````
 ** 2.1. `Scenario:` ** User is able to make registration, if he put valid data /phone number, password, email and etc./
 
          When I put valid data 
          Then I should have registration
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |


** 2.2. `Scenario:` **  User is not able to make registration, if he put invalid data /not exist phone or already registered phone or email or short password/

         When I put invalid data        1. Not exist phone -087893275145
                                        2. Not exist email – mimozaqa@abvbg
                                        3. Password with only 6 characters
         Then I should see an error message and not have a successful registration
         
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |


** 2.3. `Scenario:` ** Scenario: User is not able to make registration, if he put invalid data on Name of the user

         When I put numbers in “Име” 
         Then I should see error message 
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Failed | Failed | Failed |

-------------------------------------------------------------------------------------

### 3. Feature: Login ###
#### User story: ####
> As a user who is already registered

> I want to login 

> So that I can go to my account and offer my car.

##### Background: #####
````html
            Given I navigate to the Home page – http://www.cars.bg
              And I go to “Меню” and select "Вход/Регистрация”
              And I click on “Частно лице”  
````
** 3.1. `Scenario:` **  User is able to login

           When I put valid data - phone number and password
            And I select “Вход“
           Then I should login
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |
           
  ** 3.2. `Scenario:` ** User is NOT able to login, if there is invalid data
  
            When I put valid phone number ;
             And I put invalid password – Cars_123456
             And I select “Вход“
            Then I should have an error message and no login
            
| Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |
 
 ### 4. Feature:  Publish an offer  ###
#### User story: ####
> As a login user

> I want to publish offer

> So that I can sell my car.

 ** 4.1. `Scenario:` **  User is NOT able to publish offer, if he is not login.
 
            Given I navigate to the Home page – http://www.cars.bg
             When I go to “Меню” and select "+ Публикувай обява”
             Then I should be navigate to login 
             
 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |
 
 ** 4.2. `Scenario:` ** Logged user is able to offer a car by add information in order to publish
 
           Given I navigate to the Home page – http://www.cars.bg
             And I go to “Меню” and select "Вход/Регистрация”
             And I click on “Частно лице” 
             And I logged in my account          
            When I go to “Меню” 
             And I select "+ Публикувай обява”
            Then I can add information about my car in order to publish. 

 | Windows 10 Chrome | Windows 10 Firefox | Android 8.0 | 
 | --- | --- | --- |
 | Passed | Passed | Passed |
