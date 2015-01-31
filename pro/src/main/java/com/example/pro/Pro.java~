package com.example.pro;


import com.google.appengine.api.users.User;
import com.google.appengine.api.users.UserService;
import com.google.appengine.api.users.UserServiceFactory;


import java.util.Properties;

import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

import javax.servlet.ServletException;
//import javax.servlet.annotation.WebServlet;
import com.google.appengine.api.datastore.Query;
import com.google.appengine.api.datastore.PreparedQuery;
import com.google.appengine.api.datastore.Query.Filter;
import com.google.appengine.api.datastore.Query.FilterPredicate;
import com.google.appengine.api.datastore.Query.FilterOperator;


import com.google.appengine.api.datastore.DatastoreService;
import com.google.appengine.api.datastore.DatastoreServiceFactory;
import com.google.appengine.api.datastore.Entity;
import java.io.*;


/**
 * Servlet implementation class Pro
 */
//@WebServlet("/Pro")
public class Pro extends HttpServlet {
	private static final long serialVersionUID = 1L;
    //private String msg;    
    
    

	
	/*public void init(ServletConfig config) throws ServletException {
		msg="Hello World";
		  
	}*/
	// TODO Auto-generated method stub

	
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		//out.println("<p><h1>"+request.getParameter("username")+"<h1></p>");
		//out.println("<p><h1>"+request.getParameter("password")+"<h1></p>\n");
		String name=request.getParameter("std_name");
		String roll_no=request.getParameter("roll_no");
		String dob=request.getParameter("dob");
	        DatastoreService datastore = DatastoreServiceFactory.getDatastoreService();		      
		
		Entity details = new Entity("Student_Data");
		
			details.setProperty("Name",name);
			details.setProperty("RollNo",roll_no);
			details.setProperty("DOB",dob);
		
		datastore.put(details);
		      
		      
	
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request,response);
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();

		DatastoreService datastore = DatastoreServiceFactory.getDatastoreService();
		
		Query q = new Query("Student_Data");
		PreparedQuery pq = datastore.prepare(q);
		out.println("<!DOCTYPE html>");
                out.println("<html>");
	        out.println("<head>");
                out.println("<title>Student Details</title>");            
	        out.println("</head>");
	        out.println("<body>");
	    //out.println("<h1>Servlet Pro at " + request.getContextPath() + "</h1>");
	        out.println("<CENTER>");
	        out.println("<table BORDER=1 CELLPADDING=0 CELLSPACING=0 WIDTH=50% >");
	        out.println("<th>Stud Name</th>");out.println("<th>Roll No</th>");out.println("<th>Date of Birth</th>");
		
		for (Entity result : pq.asIterable()) {
		 
    			String Name = (String) result.getProperty("Name");
			String RollNo = (String) result.getProperty("RollNo");
	                String DOB = (String) result.getProperty("DOB");
	
	   	 	out.println("<tr>");
	         	out.print("<td>"+Name+"</td>");
	         	out.print("<td>"+RollNo+"</td>");
	         	out.print("<td>"+DOB+"</td>");
	         
	         	out.println("</tr>");	
	         }	   


		
		/*Connection con = null;  
		Statement stmt = null;
		ResultSet rs = null;
		
		try {
		      Class.forName("com.mysql.jdbc.Driver");
		      con = DriverManager.getConnection("jdbc:mysql://localhost/test","root","lordadmin");
		      stmt = con.createStatement();
		      rs = stmt.executeQuery("SELECT * FROM tbl_student");
		
		      while (rs.next()){
		    	  out.println("<tr>");
		          out.print("<td>"+rs.getString("stud_name")+ "</td>");
		          out.print("<td>"+rs.getString("roll_no")+ "</td>");
		          out.print("<td>"+rs.getString("DOB")+ "</td>");
		          
		          out.println("</tr>");		
		      }    
		}catch (SQLException e) {
	      throw new ServletException("Servlet Could not display records.", e);

		} catch (ClassNotFoundException e) {
	      throw new ServletException("JDBC Driver not found.", e);

		}*/
        
 	       
		out.println("</table>");
	out.println("<button onclick=\"goBack()\">Go Back</button>");
	out.println("<script>function goBack() {    window.history.back() }</script>");
        out.println("</CENTER>");
        out.println("</BODY></HTML>");
	}
}
