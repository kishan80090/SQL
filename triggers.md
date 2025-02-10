create or replace trigger passbooktrigger
after insert or delete or update on banks
for each row

begin

if(INSERTING) then

begin

insert into passbook values(Bankseq.nextval,:new.accno,:new.balance,:new.balance,'Account Opened');

end;

end if;

if(UPDATING) then

begin
if (:new.balance>:old.balance) then
begin
insert into passbook values(Bankseq.nextval,:new.accno,:new.balance-:old.balance,:new.balance,'Deposit');
end;
end if;


end;

end if;

end;



![image](https://github.com/user-attachments/assets/d527cd1e-d063-4f7e-bcc0-b58a6a72c221)
