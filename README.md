# hiveassignment14.2
Select date,temperature from temperature_data where zipcode > 300000 && zipcode < 399999 ;
select substr(date,7,4) as year, MAX(temperature) from temperature_data group by substr(date,7,4);
select MAX(temperature) from temperature_data where count(*) >=2  group by substr(date,7,4);
create view temperature_data_vw AS
select MAX(temperature) from temperature_data where count(*) >=2  group by substr(date,7,4);
INSERT OVERWRITE LOCAL DIRECTORY '/home/acadgild/tmp' ROW FORMAT '|' SELECT * FROM temperature_data_vw;
