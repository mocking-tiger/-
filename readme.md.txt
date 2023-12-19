
//get리퀘스트
fetch('https://learn.codeit.kr/api/members/')
  .then((response) => response.text())
  .then((result) => { console.log(result); });

//post리퀘스트
const newMember = {
  name: 'Tom',
  email: 'tom@codeitmall.kr',
  department: 'do nothing',
};

fetch('https://learn.codeit.kr/api/members/', {
  method: 'POST',
  body: JSON.stringify(newMember),
})
  .then((response) => response.text())
  .then((result) => { console.log(result); });

//put리퀘스트
const member = {
  name: 'Alice',
  email: 'alice@codeitmall.kr',
  department: 'marketing',
};

fetch('https://learn.codeit.kr/api/members/2', {
  method: 'PUT',
  body: JSON.stringify(member),
})
  .then((response) => response.text())
  .then((result) => { console.log(result); });


//delete리퀘스트
fetch('https://learn.codeit.kr/api/members/7', {
  method: 'DELETE',
})
  .then((response) => response.text())
  .then((result) => { console.log(result); });