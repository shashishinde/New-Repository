New-Repository
==============

My New Repository


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using BusinessLogic.ViewModels;
using System.Data.Entity;
using System.Web.Mvc;
using Data;


namespace BusinessLogic
{
   public class RpUser
    {

        db_testEntities context = null;
        public RpUser()
        {
            context = new db_testEntities();
        }
        public UserViewModel adduser(UserViewModel model)
        {
            reg data = new reg();
            if (model != null)
            {
                data.name = model.Name;
                data.email = model.Email;
                data.password = model.password;
                data.phoneno = model.password;
                data.photo = model.Photo;
                data.gender = model.Gender;
                data.dateofbirth = model.DateOfBirth;
                context.regs.AddObject(data);
                context.SaveChanges();
            }

            return model;
        }
        public List<UserViewModel> userlist()
        {
            List<UserViewModel> userlist = new List<UserViewModel>();
            var list = (from u in context.regs
                        select u);
            if (list != null)
            {
                foreach (var data in list)
                {
                    UserViewModel model = new UserViewModel();
                    model.UserId = data.UserId;
                    model.Name = data.name;
                    model.Email = data.email;
                    model.DateOfBirth = data.dateofbirth;
                    model.Gender = data.gender;
                    model.Photo = data.photo;

                    userlist.Add(model);

                }
                return userlist;
            }
            return null;

        }
        public UserViewModel update(UserViewModel model)
        {
            reg data = new reg();
            data.name = model.Name;
            data.email = model.Email;
            data.password = model.password;
            data.phoneno = model.password;
            data.photo = model.Photo;
            data.gender = model.Gender;
            data.dateofbirth = model.DateOfBirth;
            context.SaveChanges();
            return model;
        }
        public UserViewModel readuser(int UsetId)
        {
            UserViewModel model = new UserViewModel();
            var res = context.regs.FirstOrDefault(u => u.UserId == UsetId);
            if (res != null)
            {
                model.Name = res.name;
                model.Email = res.email;
                model.DateOfBirth = res.dateofbirth;
                model.Gender = res.gender;
                model.Photo = res.photo;
                model.password = res.password;
                return model;
            }
            return null;
        }

        public bool addusers(string Name, string Email, string password)
        {
            reg data = new reg();
            data.name = Name;
            data.email = Email;
            data.password = password;

            context.regs.AddObject(data);
            context.SaveChanges();
            return true;
        }


        //public bool addusers(UserViewModel model)
        //{
        //    reg data = new reg();
        //    data.name = model.Name;
        //    data.email = model.Email;
        //    data.password = model.password;

        //    context.regs.AddObject(data);
        //    context.SaveChanges();
        //    return true;
        //}

        public bool updateusers(string name, string Email, string password)
        {

            reg data = new reg();
            data.name = name;
            data.email = Email;
            data.password = password;
            context.SaveChanges();

            return true;
        }

        public List<UserViewModel> loadRpt()
        {
            //using (var db = new dbEntities())
            //{
            List<UserViewModel> rptList = new List<UserViewModel>();
            var rptGen = (from u in context.regs
                          //where ((tblsmpl.EmpCode.ToLower().Contains(param.ToLower().Trim())))

                          select u);


            if (rptGen != null)
            {
                foreach (var rptsData in rptGen)
                {
                    UserViewModel model = new UserViewModel();

                    model.Name = rptsData.name;
                    model.Email = rptsData.email;
                    model.DateOfBirth = rptsData.dateofbirth;
                    model.Gender = rptsData.gender;
                    model.Photo = rptsData.photo;
                    model.password = rptsData.password;
                    rptList.Add(model);
                    // rptList.Add(new Report() { field1 = rptsData.field1, field2 = rptsData.field2, field3 = rptsData.field3, field4 = rptsData.field4, field5 = rptsData.field5, field6 = rptsData.field6, field7 = rptsData.field7 });
                }

                return (rptList);
                //}
            }
            return null;
        }



        public List<UserViewModel> GetStudents()
        {
            //using (var db = new dbEntities())
            //{
            List<UserViewModel> rptList = new List<UserViewModel>();
            var rptGen = (from u in context.regs
                          //where ((tblsmpl.EmpCode.ToLower().Contains(param.ToLower().Trim())))

                          select u);


            if (rptGen != null)
            {
                foreach (var rptsData in rptGen)
                {
                    UserViewModel model = new UserViewModel();

                    model.Name = rptsData.name;
                    model.Email = rptsData.email;
                    model.DateOfBirth = rptsData.dateofbirth;
                    model.Gender = rptsData.gender;
                    model.Photo = rptsData.photo;
                    model.password = rptsData.password;
                    rptList.Add(model);
                    // rptList.Add(new Report() { field1 = rptsData.field1, field2 = rptsData.field2, field3 = rptsData.field3, field4 = rptsData.field4, field5 = rptsData.field5, field6 = rptsData.field6, field7 = rptsData.field7 });
                }

                return (rptList);
                //}
            }
            return null;
        }



        
    }
}
