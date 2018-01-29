# <i class="fas fa-align-left"></i> Submit to Dealer
***
Additional form variations can be found [here](https://github.com/bs-production/front-end-guidelines/tree/master/forms)
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
<style>
.left {
    float: left;
    margin: 0 20px 5px 0;
    overflow: hidden;
}
.contact_form form {
    width: 100%;
}
.contact_form.module, .contact_form.page_widget {
    float: none;
}
</style>
    <?php
    if (!empty($_POST)) {
        global $siteData, $siteDefineData;
        require_once ENV_ROOT.'/portal/libraries/formLogger.api.php';
        $logger = new formLoggerApi();
        $logger->setSiteId($siteData['site.id']);
        $logger->setSessionId($siteDefineData['cms_tracking_sessions']['session.id']);
        $logger->setFormId('form_logger_');
        $logger->setFormName('');
        $logger->setcustomEmailSubject('');
        $logger->setNotificationEmailAddresses('');    
        if ($logger->saveData($_POST)) {
            echo '<h1>Thank you!</h1>';
            echo '<p>We have received your information and will get back to you shortly.</p>';
            echo '<style>.form-block{display:none;}</style>';
        } else {
            echo '<h1>It looks like something went wrong.</h1>';
        }
    }
    ?>
<div class="row form-block">
<h1 class="center">Donation</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Sint, incidunt iusto eligendi doloremque tempora in repellendus voluptatibus nobis, corporis sapiente molestias explicabo fuga aliquam, modi illo non placeat inventore odio?</p>

    <div class="contact_form page_widget">

		<form action="" method="post" id="">

			<div class="fname">
				<label for="First_Name">First Name: <span>*</span></label>
				<input type="text" name="form_logger_Contact_First_Name" maxlength="50" class="required" id="First_Name">
			</div>
			<div class="lname">
				<label for="Last_Name">Last Name: <span>*</span></label>
				<input type="text" name="form_logger_Contact_Last_Name" maxlength="50" class="required" id="Last_Name">
			</div>
			<div class="phone">
				<label for="Phone">Phone: <span>*</span></label>
				<input type="text" name="form_logger_Contact_Phone" maxlength="50" class="required phone" id="Phone">
			</div>
			<div class="email">
				<label for="Email_Address">Email: <span>*</span></label>
				<input type="text" name="form_logger_Contact_Email" maxlength="50" class="required email" id="Email_Address">
			</div>
                <div class="address">
                    <label for="Street">Street: <span>*</span></label>
                    <input type="text" name="form_logger_Organization_Street" maxlength="50" class="required" id="Street">
                </div>
                <div class="city">
                    <label for="City">City: <span>*</span></label>
                    <input type="text" name="form_logger_Organization_City" maxlength="50" class="required" value="" id="City">
                </div>
                <div class="state">
                    <label for="form_logger_Organization_State">State: <span>*</span></label>
                        <select name="State" class="required" id="State">
                        <option value="AL">Alabama</option>
                        <option value="AK">Alaska</option>
                        <option value="AZ">Arizona</option>
                        <option value="AR">Arkansas</option>
                        <option value="CA">California</option>
                        <option value="CO">Colorado</option>
                        <option value="CT">Connecticut</option>
                        <option value="DE">Delaware</option>
                        <option value="DC">District Of Columbia</option>
                        <option value="FL">Florida</option>
                        <option value="GA">Georgia</option>
                        <option value="HI">Hawaii</option>
                        <option value="ID">Idaho</option>
                        <option value="IL">Illinois</option>
                        <option value="IN">Indiana</option>
                        <option value="IA">Iowa</option>
                        <option value="KS">Kansas</option>
                        <option value="KY">Kentucky</option>
                        <option value="LA">Louisiana</option>
                        <option value="ME">Maine</option>
                        <option value="MD">Maryland</option>
                        <option value="MA">Massachusetts</option>
                        <option value="MI">Michigan</option>
                        <option value="MN">Minnesota</option>
                        <option value="MS">Mississippi</option>
                        <option value="MO">Missouri</option>
                        <option value="MT">Montana</option>
                        <option value="NE">Nebraska</option>
                        <option value="NV">Nevada</option>
                        <option value="NH">New Hampshire</option>
                        <option value="NJ">New Jersey</option>
                        <option value="NM">New Mexico</option>
                        <option value="NY">New York</option>
                        <option value="NC">North Carolina</option>
                        <option value="ND">North Dakota</option>
                        <option value="OH">Ohio</option>
                        <option value="OK">Oklahoma</option>
                        <option value="OR">Oregon</option>
                        <option value="PA">Pennsylvania</option>
                        <option value="RI">Rhode Island</option>
                        <option value="SC">South Carolina</option>
                        <option value="SD">South Dakota</option>
                        <option value="TN">Tennessee</option>
                        <option value="TX">Texas</option>
                        <option value="UT">Utah</option>
                        <option value="VT">Vermont</option>
                        <option value="VA">Virginia</option>
                        <option value="WA">Washington</option>
                        <option value="WV">West Virginia</option>
                        <option value="WI">Wisconsin</option>
                        <option value="WY">Wyoming</option>
                </select>
            </div>
                <div class="zip">
                    <label for="Zip">Zip Code: <span>*</span></label>
                    <input type="text" name="Form_logger_Organization_Zip_Code" maxlength="10" class="required zipcode" value="" id="Zip">
                </div>

							<div class="submit">
					<input class="submit" name="send" type="submit" value="Send" id="save">
				</div>
			

		</form>
</div>

</div>
<div class="row">
<div class="panel">
    Privacy Statement: Your privacy is valued! Your personal information will be kept confidential and will not be redistributed or shared with any third parties.
    </div>
</div>
```