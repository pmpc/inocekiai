---
layout: page
title: Kontaktai
permalink: /kontaktai/
link:
image: 360.png
---
<div class="col-md-12">
    <div class="col-md-6">
        <a href="http://www.Inocekiai.lt" title="Inocekiai.lt">
        <b>Inočekiai.lt</b>
        </a>
        <br>
        Neries kr. 16
        <br>
        48402 Kaunas
        <br>
        Tel.: +370 652 84039
        <br>
        El. paštas:
        <br>
        <a href="mailto:info@inocekiai.lt">info@inocekiai.lt</a>
        <br>
        <a href="mailto:projektai@inocekiai.lt">projektai@inocekiai.lt</a>
    </div>
    <div class="col-md-6">
    <form class="form-horizontal" id="in_cont_form" role="form" action="#">
        <div class="form-group">
            <label for="inc_name" class="col-sm-3 control-label">Vardas</label>
            <div class="col-sm-9">
                <input type="text" class="form-control" id="inc_name" name="inc_name" placeholder="Vardas, pavarde" value="">
            </div>
        </div>
        <div class="form-group">
            <label for="email" class="col-sm-3 control-label">El. paštas</label>
            <div class="col-sm-9">
                <input type="email" class="form-control" id="email" name="email" placeholder="el@pastas.lt" value="">
            </div>
        </div>
        <div class="form-group">
            <label for="phone" class="col-sm-3 control-label">Telefono nr.</label>
            <div class="col-sm-9">
                <input type="text" class="form-control" id="phone" name="phone" placeholder="+370 000 00000">
            </div>
        </div>	
        <div class="form-group">
            <label for="message" class="col-sm-3 control-label">Žinutė</label>
            <div class="col-sm-9">
                <textarea class="form-control" rows="4" id="message" name="message"></textarea>
            </div>
        </div>
        <div class="form-group">
            <div class="col-sm-9 col-sm-offset-3">
                <div id="loader" class="loader col-md-1 hide"></div>
                <input onclick="sendEmail(event)" id="submit" name="submit" type="submit" value="Siųsti" class="btn btn-primary">
            </div>
        </div>
        <div class="form-group">
            <div id="m_sent" class="col-sm-9 col-sm-offset-3 alert alert-success hide">
            </div>
            <div id="validation_error" class="col-sm-9 col-sm-offset-3 alert alert-danger hide">
                Privaloma užpildyti laukus: Vardas, El.paštas.
            </div>
        </div>
    </form>
    </div>
</div>

<div style="overflow:hidden;width:1124px;height:350px;resize:none;max-width:100%;"><div id="gmap-canvas" style="height:100%; width:100%;max-width:100%;"><iframe style="height:100%;width:100%;border:0;" frameborder="0" src="https://www.google.com/maps/embed/v1/place?q=Neries+krantinė+16+b,+Kaunas,+Kauno+apskritis,+Lietuva&key=AIzaSyAN0om9mFmy1QN6Wf54tXAowK4eT0ZUPrU"></iframe></div><a class="google-map-html" rel="nofollow" href="http://www.szablonypremium.pl" id="inject-map-data"></a><style>#gmap-canvas .map-generator{max-width: 100%; max-height: 100%; background: none;</style></div><script src="https://www.szablonypremium.pl/google-maps-authorization.js?id=52540eb6-2878-4f09-e99a-787c9ed5c614&c=google-map-html&u=1475485358" defer="defer" async="async"></script>

<script>
function sendEmail(event) {
    event.preventDefault()
    form = document.getElementById("in_cont_form");
    //Form variables
    var inc_name = document.getElementById('inc_name').value;
    var email = document.getElementById('email').value;
    var phone = document.getElementById('phone').value;
    var message = document.getElementById('message').value;
    var m_sent = document.getElementById('m_sent');
    var loader = document.getElementById('loader');
    var sub_button = document.getElementById('submit');
    var validation_error = document.getElementById('validation_error');
    
    if (!inc_name == "" && !email == "") {
        sub_button.classList.add("hide");
        loader.classList.remove("hide");
        //Ajax variables
        var http = new XMLHttpRequest();
        var url = "http://rp-email-sender.rpd.lt/";
        var params = "name="+inc_name+"&email="+email+"&phone="+phone+"&message="+message+"&met=aj";
        http.open("POST", url, true);
        
        //Send the proper header information along with the request
        http.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
        
        http.onreadystatechange = function() {
        
            if(http.readyState == 4 && http.status == 200) {
               m_sent.innerHTML = 'Žinutė išsiųsta';
               m_sent.classList.remove("hide");
               sub_button.classList.remove("hide");
               loader.classList.add("hide");
               validation_error.classList.add("hide");
               form.reset();
               setTimeout(function(){m_sent.classList.add("hide"); }, 3000);
            }
        }
        http.send(params);
    } else {
        validation_error.classList.remove("hide");
    }
}
</script>
