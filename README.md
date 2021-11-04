# detay
hesapmakinesi
//html kodları

<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title> Berkay Güven Çağlar'ın Hesap Makinesi</title>
	<link rel="stylesheet" href="../4.11.2021/style.css">
</head>
<body>
	<div class="sayfa">
		<center><font size="5" face="Cooper Black" color="black">Hesap Makinesi V1.0</font></center>
		<table>
			<tr>
				<td colspan="5" id="islem"></td>
			</tr>
			<tr>
				<td colspan="5" id="gosterge">0</td>
			</tr>
			<tr>
				<td class="btn btnRakam">7</td>
				<td class="btn btnRakam">8</td>
				<td class="btn btnRakam">9</td>
				<td class="btn btnOpt">/</td>
				<td class="btn btnCE">CE</td>
			</tr>
			<tr>
				<td class="btn btnRakam">4</td>
				<td class="btn btnRakam">5</td>
				<td class="btn btnRakam">6</td>
				<td class="btn btnOpt">*</td>
				<td class="btn btnC">C</td>
			</tr>
			<tr>
				<td class="btn btnRakam">1</td>
				<td class="btn btnRakam">2</td>
				<td class="btn btnRakam">3</td>
				<td class="btn btnOpt">-</td>
				<td rowspan="2" class="btn btnEsit">=</td>
			</tr>
			<tr>
				<td colspan="2" class="btn btnRakam">0</td>
				<td class="btn btnNokta">.</td>
				<td class="btn btnOpt">+</td>
			</tr>
		</table>
	</div>
<script src="script.js"></script>
</body>
</html>
//html kodları son..






//CSS KODLARI
body{
    background-image: url(../4.11.2021/arkaplan.jpg);
}
.sayfa{
    width:360px;
    margin:auto;
}
table{
    background:#ffffff;
    border-spacing: 10px;
    text-align: center;
}

 .btn{
    width: 60px;
    background:rgb(0, 0, 0);
    text-align: center;
    line-height: 60px;
    color:#fff;
    font-size: 1.5em;
}
.btn:hover{
    background-color: rgb(255, 0, 0);
}
#islem, #gosterge{
    padding:5px;
    text-align: right;
}

#gosterge{
    height: 60px;
    background:#ddfafa;
    color:#333;
    font-size: 1.8em;
    text-align: right;
    line-height: 40px;
    padding:10px;
    box-sizing: border-box;
}
#islem{
    background:gray;
}
//CSS KODLARI SON..



//JS KODLARI


//genel değişkeni oluşturmak.
var optDurum=false,opt="",sonuc=0;
//nesnelerin oluşturmak için kullandığım kodlar.
var btnrakam=document.querySelectorAll(".btnRakam");//rakamlar
var gosterge=document.querySelector("#gosterge");//gösterge paneli
var btnOpt=document.querySelectorAll(".btnOpt");//işlem butonları
var islem=document.querySelector("#islem");
var btnC=document.querySelector(".btnC");
var btnCE=document.querySelector(".btnCE");
var btnEsit=document.querySelector(".btnEsit");
var btnNokta=document.querySelector(".btnNokta");

//butonlara basıldı kontrolü
btnrakam.forEach(function(element){

    element.onclick=function(e){

        //baştaki 0 değerini kaldırmak için ve opt basılıp basılmadığını da kontrol etmek için.
        if(gosterge.textContent=="0" || optDurum)
        gosterge.textContent="";

        //test nesnesini okuyup td içindeki değerlerle birleştirecek kod.
        
        gosterge.textContent+=this.textContent;
        optDurum=false; //+ ,- gibi operatör işlemi yapıldıysa text kutusunu sıfırlaması gerekiyor.
    }

});

btnOpt.forEach(function(element){
element.onclick=function(e){
optDurum=true;
var yeniOpt=this.textContent;
//islem paneli
islem.textContent=islem.textContent+" "+gosterge.textContent+" "+yeniOpt;

//sonucu yazdırmak.
switch(opt) //hafızadaki opt işlemi
{
case "+":gosterge.textContent=(sonuc + Number(gosterge.textContent));break;
case "-":gosterge.textContent=(sonuc - Number(gosterge.textContent));break;
case "*":gosterge.textContent=(sonuc * Number(gosterge.textContent));break;
case "/":gosterge.textContent=(sonuc / Number(gosterge.textContent));break;
default:break;
}
sonuc=Number(gosterge.textContent);
opt=yeniOpt;

}

});

btnC.onclick=function(e){
gosterge.textContent="0";
}
btnCE.onclick=function(e){
gosterge.textContent="0";
islem.textContent="";
sonuc=0;
opt="";
}
btnEsit.onclick=function(e)
{
islem.textContent="";
optDurum=true;
//sonucu yazdırmak
switch(opt) //hafızadaki opt işlemi
{
case "+":gosterge.textContent=(sonuc + Number(gosterge.textContent));break;
case "-":gosterge.textContent=(sonuc - Number(gosterge.textContent));break;
case "*":gosterge.textContent=(sonuc * Number(gosterge.textContent));break;
case "/":gosterge.textContent=(sonuc / Number(gosterge.textContent));break;
default:break;
}
sonuc=Number(gosterge.textContent);
gosterge.textContent=sonuc;
sonuc=0;
opt="";
}
btnNokta.onclick=function(e)
{
if(!optDurum && !gosterge.textContent.includes("."))
{
gosterge.textContent+=".";
}
else if(optDurum)
{
gosterge.textContent="0";
}
if(!gosterge.textContent.includes("."))
{
gosterge.textContent+=".";
}
optDurum=false;
}
//JS KODLARI SONY..
