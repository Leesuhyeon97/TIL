<h1>ID 유효성 검사</h1>


<h3>1. 소문자로 바꾸기</h3>
new_id = new_id.`toLowerCase();`

<h3>2. 특정문자 제외하고 다 지우기</h3>
for (int i=0; i<new_id.length(); i++){  
char ch = new_id.charAt(i);  
if(Character.isAlphabetic(ch)|| //영문자확인  
Character.isDigit(ch)|| //숫자 확인  
ch == '-'||ch == '_'||ch == '.') // '-', '_', '.' 확인  
answer += ch;  
}  
<h3>3. 마침표 2개 연속되는것은 한개로 치환하기</h3>
while (answer.indexOf("..") != -1)  
answer = answer.replace("..",".");  
<h3>4. 마침표가 처음이나 끝에 존재하면 제거</h3>
if (!answer.isEmpty() && answer.charAt(0) == '.')  
answer = answer.substring(1);  
if (!answer.isEmpty() && answer.charAt(answer.length() - 1) == '.')  
answer = answer.substring(0,answer.length() - 1);  
<h3>5. ID가 빈 문자열일때 a를 삽입</h3>
if(answer.isEmpty())  
answer = "a";  
<h3>6. ID가 16자리이상이면 15자리까지 그 뒤의 문자 제거,   
마지막 글자가 마침표면 마침표도 제거</h3>
if(answer.length()>15){  
answer = answer.substring(0,15);  
if(answer.charAt(answer.length()-1)=='.')  
answer= answer.substring(0,answer.length()-1);  
}
<h3>7. ID가 2자리 이하면, 마지막 문자를 반복해 3자리를 만듦</h3>
while (answer.length()<3)  
answer += answer.charAt(answer.length()-1);  
return answer;  
}  
}