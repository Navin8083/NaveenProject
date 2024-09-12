package com.SpringWeb.SpringWeb;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class Controller1 {
    
    @RequestMapping(value = "/login", method = RequestMethod.GET)
    public ModelAndView showLogin() {
        return new ModelAndView("login");
    }
// Awesh Edit
    @RequestMapping(value = "/login", method = RequestMethod.POST)
    public ModelAndView login(@RequestParam("username") String username, @RequestParam("password") String password) {
        // Hardcoded for simplicity; replace with database authentication in real applications
        if ("admin".equals(username) && "password".equals(password)) {
            ModelAndView mv = new ModelAndView("welcome");
            mv.addObject("username", username);
            return mv;
        } else {
            ModelAndView mv = new ModelAndView("login");
            mv.addObject("error", "Invalid username or password");
            return mv;
        }
    }
}
