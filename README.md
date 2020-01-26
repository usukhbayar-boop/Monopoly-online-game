# Monopoly-online-game
online game
<!DOCTYPE html>
<html>
    <head>
        <title>Hamburger Game</title>
        <link href="customer.css" type="text/css" rel="stylesheet">
    </head>
    <body>
    <!--
            orts tus bur deer ud bolon class uusgesen
        -->
    <div id="fullGame">
        <div id="slide1">
            <div id="buttons">
                <button id="it1" class="item" onclick="finish()">Бургерээ дуусгах</button>
                <button class="item" id="it2" onclick="elemenT('meat',3,4)">Мах нэмэх</button>
                <button class="item" id="it3" onclick="elemenT('cheese',1,2)">Бяслаг нэмэх</button>
                <button class="item" id="it4" onclick="elemenT('green',1.2,1)">Салад нэмэх</button>
                <button id="it5" class="item" onclick="elemenT('ketchup',.5,1)">Кетчуп нэмэх</button>
                <button class="item" id="it6" onclick="elemenT('onion',.35,1)">Сонгино нэмэх</button>
                <button class="item" id="it7" onclick="elemenT('egg',1.5,3)">Өндөг нэмэх</button>
                <button onclick="prices('1')" class="item" id="it8">Prices</button>
            </div>
            <p id="cost">Cost: </p>
            <div id="prices">
                <button id="close" onclick="prices('0')">X</button>
                <h2>Зардал</h2>
                <br />
                <p>Кетчуп 1$</p>
                <p>Сонгино 1$</p>
                <p>Бяслаг 2$</p>
                <p>Өндөг 3$</p>
                <p>Салад 1$</p>
                <p>Мах 4$</p>
                <br />
                <h2>Дүрэм</h2>
                <p>Хэрэглэгчийн мөнгөнд тааруулж бургерийг бэлдэнэ</p>
                <br />
                <h2>Example 1</h2>
                <p>Үйлчлүүлэгчид 20$ байна</p>
                <p>Бургер 8$ болсон байна</p>
                <p>Хэрэглэгч бухимдалтай байна</p>
                <p>Оноо - 8</p>
                <h2>Example 2</h2>
                <p>Хэрэглэгчид 20$ байна</p>
                <p>Бургер 13$ үнэтэй</p>
                <p>Үйлчлүүлэгч сэтгэл хангалуун байна.</p>
                <p>Өмнөх оноо + 20 - 13</p>
                
            </div>
            
            <div id="sandwich"></div>    
            <div id="leftSide"></div>
            <div id="rightSide"></div>
            <div id="bottomSide"></div>
            <div id="topSide"></div>
        </div>
    
        <div id="slide2">
            <div id="leftSide2"></div>
            <div id="rightSide2"></div>
            <div id="bottomSide2"></div>
            <div id="topSide2"></div>
            <button id="start" onclick="begin()">Эхлэх</button>
            <img src='https://imgur.com/TErAL9v.jpg' id="customer">
            <p id="customerMessage"></p>
            <p id="profit">Нийт: 0</p>
            <img src="https://imgur.com/Izyt8cf.jpg" id="mark">
            <img id="bottle" src="https://imgur.com/NArkZ81.jpg">
        </div>
    </div>
    
    <div id="middle">
            <p id="how1">Ачаалж байна</p>
            <div id="round"></div>
        </div>
    <script type="text/javascript">
        var size=50;
var usedThings=0;
var total=0;

function elemenT(x,t,cash){
    size-=t/2;
    var el = document.createElement("div");
    document.getElementById("sandwich").appendChild(el);
    el.id = x;
    el.style.top=`${size}vmin`
    size-=t/2;
    usedThings+=parseInt(cash);
    document.getElementById("cost").innerText=`Cost: ${usedThings}$`;
}

var customerCash;
function customer(p){
    customerCash=Math.floor(Math.random()*25)+5;
    //uilchluulegche orhih
    setTimeout(function(){
        document.getElementById('customer').style.left=`${p}%`;
    },500);
}

function finish(){
    size-=3.5/2;
    var el = document.createElement("div");
    document.getElementById("sandwich").appendChild(el);
    el.id = "bread";
    el.style.top=`${size}vmin`;
    el.style.borderRadius="50vmax 50vmax 10vmax 10vmax";
    el.style.borderBottom="none";
    el.style.borderTop="2px dotted #a86";
    size-=3.5/2;
    //uilchluulegchid hool taalagdaagui bol munguu aldana
    if(customerCash>(usedThings*2)){total-=customerCash;}
    total+=customerCash-usedThings;
    document.getElementById("profit").innerText=`Total: ${total}$`;
    usedThings=0;
    document.getElementById("customerMessage").innerText="";
    document.getElementById("slide1").style.left="-100%";
    document.getElementById("slide2").style.left="0";
    document.getElementById('start').style.display="none";
    setTimeout(function(){
        document.getElementById('sandwich').style.transform='scale(1.1)';
    document.getElementById('sandwich').style.opacity="0";
    //uilchllegchiig orhih
    setTimeout(function(){
        document.getElementById('customer').style.left=`80%`;
    },500);
        
        //shine iulchluulegch
        setTimeout(function(){
            
            customer('25');
            setTimeout(function(){
                document.getElementById('start').style.display="block";
                setTimeout(function(){
                    document.getElementById("customerMessage").innerText=`Сайн байна уу надад ${customerCash}$. байна. Үүнд тааруулаад бургер хийж өгөөч :)`;
                },250);
            },1000);
        },Math.random()*2000+1000);
    },1500);
}

function begin(){
    size=50;
    //umnuh hooloo ustgah
    for(k=0; k<document.getElementById("sandwich").getElementsByTagName("div").length;k++){
        document.getElementById("sandwich").getElementsByTagName("div")[k].style.display="none";
    }
    document.getElementById('sandwich').style.transform='scale(1.5)';
    document.getElementById('sandwich').style.opacity="1";
    setTimeout(function(){
        elemenT("bread",3.5,0);
    },1000);
    document.getElementById("buttons").style.display="block";
    document.getElementById("slide1").style.left="0";
    document.getElementById("slide2").style.left="100%";
}

function prices(t){
    document.getElementById("prices").style.transform=`translate(-50%, -50%) scale(${t})`;
}

window.onload=function(){
    document.getElementById("how1").innerText="Open"
    document.getElementById("middle").style.opacity="0";
    setTimeout(function(){
        document.getElementById("middle").style.display="none";
        customer('25');
    document.getElementById('start').style.display="block";
    setTimeout(function(){
                    document.getElementById("customerMessage").innerText=`Сайн байна уу. Надад ${customerCash}$. байна. Үүнд тааруулаад бургер хийж өгөөч :)`;
    },250);
    document.getElementById("fullGame").style.display="block";
    },1000);
};


    </script>
    </body>
</html>
