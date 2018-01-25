# Direct to Portal
For your form you need to name your inputs `"f_l_"`, any form inputs should be named accordingly.  
Additional examples can be found [here](https://github.com/bs-production/front-end-guidelines/tree/master/forms)

``` php
  <link href="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/css/datepicker.min.css" rel="stylesheet" type="text/css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/js/datepicker.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/js/i18n/datepicker.en.js"></script>
        
<script type="text/javascript" src="/core/js/jquery.validate.js"></script>
<script type="text/javascript">
$(document).ready(function(){
    jQuery.validator.addMethod('notEqualTo', function(value, element, param) {
        return this.optional(element) || value != $(param).val();
    }, 'First and last name cannot be the same.');
    
            jQuery.validator.addMethod('zip', function(zip, element) {
            return this.optional(element) || zip.match(/(^\d{5}(-\d{4})?$)$/);
        }, 'Please enter a valid zip code.');
        
        jQuery.validator.addMethod('phone', function(phone, element) {
            return this.optional(element) || phone.match(/^[01]?[- .]?\(?[2-9]\d{2}\)?[- .]?\d{3}[- .]?\d{4}$/);
        }, 'Please enter a valid phone number.');
            $('#contact_form').validate({
        rules: {
            Email_Address: {
                email: true
            },
            First_Name : {
                notEqualTo: '#Last_Name'
            },
            Zip_Code: {
                zip: true
            },
            Phone: {
                phone: true
            }
        }
    });
        $('#contact_form').submit(function() {
        if($('#contact_form').valid() === true)
        {
            $('#contact_form .submit').attr('disabled', 'disabled');
        }
    });
});
</script>
<?php
    if (!empty($_POST)) {
        global $siteData, $siteDefineData;
        require_once ENV_ROOT.'/portal/libraries/formLogger.api.php';
        $logger = new formLoggerApi();
        $logger->setSiteId($siteData['site.id']);
        $logger->setSessionId($siteDefineData['cms_tracking_sessions']['session.id']);
        $logger->setFormId('f_l_');
        $logger->setFormName('');
        $logger->setcustomEmailSubject('');
        $logger->setNotificationEmailAddresses('');    
        if ($logger->saveData($_POST)) {
            echo '<h1>Thank you!</h1>';
            echo '<p>We have received your information and will get back to you shortly.</p>';
            echo '<style>.contact_form{display:none;}</style>';
        } else {
            echo '<h1>It looks like something went wrong.</h1>';
        }
    }
    ?>

<?php


<div class="right contact_form page_widget">
<h3 class="center">Request Your Appointment Now</h3>
    <form action="" method="post" id="contact_form">
        <div class="fname">
            <label for="First_Name">First Name: <span>*</span></label>
            <input type="text" name="f_l_First_Name" maxlength="50" class="required" id="First_Name">
        </div>
        <div class="lname">
            <label for="Last_Name">Last Name: <span>*</span></label>
            <input type="text" name="f_l_Last_Name" maxlength="50" class="required" id="Last_Name">
        </div>
        <div class="address">
            <label for="Street">Street: <span>*</span></label>
            <input type="text" name="f_l_Street" maxlength="50" class="required" id="Street">
        </div>
        <div class="city">
            <label for="City">City: <span>*</span></label>
            <input type="text" name="f_l_City" maxlength="50" class="required" value="" id="City">
        </div>
        <div class="state">
            <label for="State">State: <span>*</span></label>
            <select name="f_l_State" class="required" id="State">
                <option value="" selected="selected">Please select...</option>
                <option value="CT">Connecticut</option>
                <option value="NY">New York</option>
            </select>
        </div>
        <div class="zip">
            <label for="Zip">Zip Code: <span>*</span></label>
            <input type="text" name="f_l_Zip_Code" maxlength="10" class="required zipcode" value="" id="Zip">
        </div>
        <div class="phone">
            <label for="Phone">Phone: <span>*</span></label>
            <input type="text" name="f_l_Phone" maxlength="50" class="required phone" id="Phone">
        </div>
        <div class="email">
            <label for="Email_Address">Email: <span>*</span></label>
            <input type="text" name="f_l_Email_Address" maxlength="50" class="required email" id="Email_Address">
        </div>

        <div class="date-requested">
            <p>Please select your availability:</p>

            <div class="left small-6">
                <label for="custom_field_3">Preferred Appointment:<span class="date-required">*</span></label>
                <div>
                  <input type="text"  id="datepicker" name="f_l_Preferred_Appointment_Date_1" maxlength="50" class="required" value="Select Date">
                </div>          
            </div>
            <div class="small-6" style="display: inline;">
                <select name="f_l_Preferred_Appointment_Time_1" class="required" id="time1" style="margin-top:17px; width: 140px;">
                    <option value="">Arrival Window</option>
                    <option value="9am-1pm">9am-1pm</option>
                    <option value="1pm-5pm">1pm-5pm</option>
                </select>
            </div>

        </div>
        <div class="date-requested">
                <div class="left small-6">
                <div>
                  <input type="text"  id="datepicker2" name="f_l_Preferred_Appointment_Date_2" maxlength="50" class="required" value="Select Date">
                </div>          
            </div>

            <div class="small-6" style="display: inline;">
                <select name="f_l_Preferred_Appointment_Time_2" class="required" id="time1" style="margin-top:17px; width: 140px;">
                    <option value="">Arrival Window</option>
                    <option value="9am-1pm">9am-1pm</option>
                    <option value="1pm-5pm">1pm-5pm</option>
                </select>
            </div>

        </div>
        <div class="date-requested">
            <div class="left small-6">
                <div>
                  <input type="text"  id="datepicker3" name="f_l_Preferred_Appointment_Date_3" maxlength="50" class="required" value="Select Date">
                </div>          
            </div>
            <div class="small-6" style="display: inline;">
                <select name="f_l_Preferred_Appointment_Time_3" class="required" id="time1" style="margin-top:17px; width: 140px;">
                    <option value="">Arrival Window</option>
                    <option value="9am-1pm">9am-1pm</option>
                    <option value="1pm-5pm">1pm-5pm</option>
                </select>
            </div>

        </div>
        <div class="comment">
            <label for="Message">Comments:</label>
            <textarea value="Comments:" name="f_l_Message" id="Message"></textarea>
        </div>
        <div class="g-recaptcha" data-sitekey="6LeDRjQUAAAAAFnMLuC2cA_aajyhPOdnahHiS5Zt"></div>
        <div class="submit">
            <input class="submit" name="send" type="submit" value="Send" id="save">
        </div>
    </form>
</div>

<?php } ?>



<script>
$('#datepicker, #datepicker2, #datepicker3').datepicker({
    language: 'en',
    onShow: function(dp, animationCompleted){
         
    },
    onHide: function(dp, animationCompleted){
         
    }
})

var disabledDays = [0, 6];

$('#datepicker, #datepicker2, #datepicker3').datepicker({
    language: 'en',
    onRenderCell: function (date, cellType) {
        if (cellType == 'day') {
            var day = date.getDay(),
                isDisabled = disabledDays.indexOf(day) != -1;

            return {
                disabled: isDisabled
            }
        }
    }
})

$(document).ready(function(){
       $("#datepicker, #datepicker2, #datepicker3").val('Select A Date');
    });
    
</script>
```